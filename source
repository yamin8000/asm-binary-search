;yamin8000 2017 
;Binary Search

INCLUDE emu8086.inc

org 100h

;Printing Message
lea si,msg
call print_string

;Data Entry Loop Properties
mov bx,05h
lea si,array

;Data Entry Loop
arrayloop: call scan_num
call clear_screen
mov [si],cx
inc si
dec bx
jnz arrayloop
;Data Entry Loop

;Selection Sort Procedure Call, Sorting Array For Binary Search
mov si,00h
call selection

;Data Entry & Data Sort Ended

;Binary Search Procedure Call
call binary

ret

msg db "Enter Array Elements:",0       ;Array Entry Message
msgtarget db "Enter Search Target:",0  ;Target Entry Message
msgfound db "Found!",0                 ;Found Message
msgnfound db "Not Found!",0            ;Not Found Message 
array db 5 dup(?)                      ;Array
i dw ?                                 ;Selection Sort
j dw ?                                 ;Selection Sort
n dw 0004h                             ;Selection Sort
min dw ?                               ;Selection Sort
low dw 0000h                           ;Binary Search Low Boundary
high dw 0004h                          ;Binary Search High Boundary
mid dw ?                               ;Binary Search Suspect!(Medium)
target dw ?                            ;Binary Search Target

DEFINE_SCAN_NUM
DEFINE_PRINT_STRING
DEFINE_CLEAR_SCREEN
DEFINE_PRINT_NUM_UNS
DEFINE_PRINT_NUM

;Selection Sort Procedure
selection proc
    lea bx,array
    mov i,00h
    for1: mov cx,i
    mov min,cx
    mov j,cx
    for2: inc j
        mov si,min
        mov al,[bx+si]
        mov si,j
        mov ah,[bx+si]
        cmp al,ah
        jl jump
        mov cx,j
        mov min,cx
        jump: mov cx,j
        cmp cx,n
        jne for2
    mov si,i
    mov cl,[bx+si]
    mov si,min
    mov ch,[bx+si]
    mov [bx+si],cl
    mov si,i
    mov [bx+si],ch
    inc i
    mov cx,i
    cmp cx,n
    jne for1
    ret          
;Selection Sort Procedure

;Binary Search Procedure
    binary proc
    lea si,msgtarget
    call print_string
    call scan_num
    mov target,cx 
    
    while: mov ax,low
    mov bx,high
    
    ;While Low<High
    cmp ax,bx
    jg endwhile    ;Jump Greater, Ending While 

	;Calculating Medium Index
    mov ax,low
    add ax,high
    mov dl,0002h
    div dl
    mov ah,0000h ;Zeroing Division's Remainder
    mov mid,ax
    mov bx,ax
    lea si,array
    mov dx,[si + bx]
    mov dh,0000h
    
    ;ax = mid index
    ;dx = mid value
    
    mov bx,target
    
    ;array[mid]=target?
    cmp dx,bx
    je EqualToMid
    jne NotEqualToMid
    
    ;array[mid] is Equal To Target!Found!
    EqualToMid: call clear_screen
    lea si,msgfound
    call print_string
    ret
    
    ;array[mid] is not Equal To Target, Either Greater Or Lesser 
    NotEqualToMid: jg Greater
                   jl Lesser
    
    Greater: dec mid    ;Left Side Sub-Array
    mov dx,mid
    mov high,dx
    jmp while
    
    Lesser: inc mid     ;Right Side Sub-Array
    mov dx,mid
    mov low,dx
    jmp while
    
    endwhile: call clear_screen
    lea si,msgnfound
    call print_string 
    ret
;Binary Search Procedure    

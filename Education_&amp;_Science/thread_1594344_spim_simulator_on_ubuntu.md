---
title: "spim simulator on ubuntu"
date: 2010-10-12
forum: Education &amp; Science
---

### Post by blob84 on 2010-10-12
Hi, i have installed spim but i doesn't load the asm file,
This is the file:
I use this command to load ```
load "add2.asm"
``` or ```
load "home/dir/add2.asm"
```, but nothing happens.
[PHP]# add2.asm
# somma 2 numeri dati in input

# registri usati
#    $t0 - usato per contenere il primo numero
#    $t1 - usato per contenere il secondo numero
#    $t2 - usato per contenere la somma di $t0 e $t1
#    $v0 - syscall e valore di ritorno
#    $a0 - syscall

main:
    ## ottieni il primo numero 
    li     $v0, 5     # chiama una syscall
    syscall     # crea la syscall
    move     $t0, $v0     # sposta il numero letto in $t0
    
    ## ottieni il secondo numero
    li     $v0, 5     # chiama una syscall
    syscall     # crea la syscall
    move     $t1, $v0     # sposta il numero letto in $t0
    
    add     $t2, $t0, $t1 # effettua la somma

    ## Stampa $t2
    move     $a0, $t2     # sposta il numero per stamparlo in $a0
    li     $v0, 1    # chiama la syscall per stampare $v0
    syscall

    li     $v0, 10    # syscall codice 10 per uscire
    syscall     # crea la syscall

# end of add2.asm.
[/PHP]
It works, i forgot the command run! :oops:

---


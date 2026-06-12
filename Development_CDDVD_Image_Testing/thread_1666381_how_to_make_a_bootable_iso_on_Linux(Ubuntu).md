---
title: "how to make a bootable iso on Linux(Ubuntu)?"
date: 2011-01-13
forum: Development CD/DVD Image Testing
---

### Post by piyush.neo on 2011-01-13
i am trying to write a boot loader(hello world). i am using Bochs for simulation. But i am unable to make an bootable iso for my binary file. Though in tutorial  VFD is used but it is for windows platform. Here is my code for bootloader ( just for testing)
```

;*********************************************
;    Boot1.asm
;        - A Simple Bootloader for testing if cd is booting or not
;
;    Operating Systems Development Tutorial
;*********************************************
 
[BITS 16]    ;tell the assembler that its a 16 bit code
[ORG 0x7C00]    ;Origin, tell the assembler that where the code will

Start:
 
    cli                    ; Clear all Interrupts
    hlt                    ; halt the system
    
times 510 - ($-$$) db 0                ; We have to be 512 bytes. Clear the rest of the bytes with 0
 
dw 0xAA55                    ; Boot Signiture

```

i tried master ISO. It is converting the binary file to ISO but not to bootable ISO. Bochs is showing error* "cd is not eltorito" *which i googled and found to be standard for bootable ISO.
Can anyone suggest a reliable application to make a bootable ISO on Ubuntu?
My work is stuck due to this...

---


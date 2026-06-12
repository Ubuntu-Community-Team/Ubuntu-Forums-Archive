---
title: "planeshift game"
date: 2009-01-21
forum: General Help
---

### Post by thingy87654321 on 2009-01-21
how do i get the .deb file for planeshift? i click the download link for linux and it gives me a .bin file, can i run .bin files?

---

### Post by taurus on 2009-01-21
Yes, you can install the .bin.  Save it to your desktop and then open a terminal and run

Applications -> Accessories -> Terminal
```
cd ~/Desktop
chmod +x *filename*.bin
./*filename*.bin
```
Replace *filename* with the real name of the file.

---

### Post by thingy87654321 on 2009-01-21
thanks dude

---

### Post by binbash on 2009-01-21
you won't find any deb files for planeshift.Follow taurus's way

---

### Post by thingy87654321 on 2009-01-21
it says "installer payload intilazation failed" what does that mean? and how do i fix it?

---

### Post by Henrikzhura on 2009-03-12
This worked for me:

mkdir ~/.Games
cd ~/Desktop
chmod +x PlaneShift_CBV0.3.020-x86.bin
sudo ./PlaneShift_CBV0.3.020-x86.bin

---

### Post by Nempis on 2009-03-26
I could make the binfile executable, but it doesn't run it. I tried several options what should i do?
elvis@elviksenkone:~$ ./PlaneShift-v0.4.03-x64.bin
bash: ./PlaneShift-v0.4.03-x64.bin: cannot execute binary file
elvis@elviksenkone:~$ PlaneShift-v0.4.03-x64.bin
bash: PlaneShift-v0.4.03-x64.bin: command not found
elvis@elviksenkone:~$ sudo ./PlaneShift-v0.4.03-x64.bin
[sudo] password for elvis: 
./PlaneShift-v0.4.03-x64.bin: 3: Syntax error: ")" unexpected

---

### Post by Henrikzhura on 2009-07-04
> **Nempis said:**
> I could make the binfile executable, but it doesn't run it. I tried several options what should i do?
elvis@elviksenkone:~$ ./PlaneShift-v0.4.03-x64.bin
bash: ./PlaneShift-v0.4.03-x64.bin: cannot execute binary file
elvis@elviksenkone:~$ PlaneShift-v0.4.03-x64.bin
bash: PlaneShift-v0.4.03-x64.bin: command not found
elvis@elviksenkone:~$ sudo ./PlaneShift-v0.4.03-x64.bin
[sudo] password for elvis: 
./PlaneShift-v0.4.03-x64.bin: 3: Syntax error: ")" unexpected

Make sure you're in the right directory. Move the Planeshift file to your desktop or wherever and use the cd command to change it to that directory.

---


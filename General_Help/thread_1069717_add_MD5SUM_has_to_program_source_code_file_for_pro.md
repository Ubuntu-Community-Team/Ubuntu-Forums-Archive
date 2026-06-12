---
title: "add MD5SUM has to program source code file for project"
date: 2009-02-14
forum: General Help
---

### Post by e24ohm on 2009-02-14
Folks,
I want to encode or md5sum hash my source code for my programming class. My file is a simple .txt document, so how do i encode/encrypt the file with md5sum hash to authenticate its integrity for my instructure?

I am not sure how to do this so any help will be welcomed. I coded my project in Nano, so i am not sure if i am able to encode my file with md5sum hash.

I understand that md5sum has some security limitations now, so how would I do the same for sh1sum?


thank you
E

---

### Post by geirha on 2009-02-14
Do you want the people you send the code to to be able to verify the integrity of the code, or do you want the code to be encrypted/protected so that no one else can see the code?

If you just want it to be verifyable, then
```
cd /path/to/code
find -type f -not -name MD5SUMS -print0 | xargs -0 md5sum >MD5SUMS

```
This will create a file, MD5SUMS, containing the md5sum of each file. When the people recieves the code along with that file, they can run ```
md5sum -c MD5SUMS
``` to confirm that the files are intact.

If you want the code to be encrypted so that no one else can view the code, just put it in a password protected zip-file. If you want really good encryption, I suggest using PGP, but that requires that the person you want to send to already has a PGP keypair, and that you have the public key of that keypair to encrypt with.

---

### Post by e24ohm on 2009-02-14
> **geirha said:**
> Do you want the people you send the code to to be able to verify the integrity of the code, or do you want the code to be encrypted/protected so that no one else can see the code?

If you just want it to be verifyable, then
```
cd /path/to/code
find -type f -not -name MD5SUMS -print0 | xargs -0 md5sum >MD5SUMS

```
This will create a file, MD5SUMS, containing the md5sum of each file. When the people recieves the code along with that file, they can run ```
md5sum -c MD5SUMS
``` to confirm that the files are intact.

If you want the code to be encrypted so that no one else can view the code, just put it in a password protected zip-file. If you want really good encryption, I suggest using PGP, but that requires that the person you want to send to already has a PGP keypair, and that you have the public key of that keypair to encrypt with.Thank you for the help - I want to just have it so individuals can verify the file/code.

I do not understand your example, so i do applogize. Can you help me with filling in the blanks.

I have my .txt file in the following location /home/E/Documents/C_program
cpro.txt is the name of my file. Can i even do the source code for the app? If so how do i fille in the infromation with the detiails you supplied me. Thank you again, sorry if this is a stupid question, just not following along.

```
cd /path/to/code
find -type f -not -name MD5SUMS -print0 | xargs -0 md5sum >MD5SUMS

```

---

### Post by geirha on 2009-02-14
> **e24ohm said:**
> 
I have my .txt file in the following location /home/E/Documents/C_program
cpro.txt is the name of my file. Can i even do the source code for the app? If so how do i fille in the infromation with the detiails you supplied me. Thank you again, sorry if this is a stupid question, just not following along.

I don't quite understand what the purpose of that .txt-file is, but with the information given, doing the following will create /home/E/Documents/C_program/MD5SUMS with the md5sums of all files (in all subdirectories) of /home/E/Documents/C_program/:

```
cd "/home/E/Documents/C_program"
find -type f -not -name MD5SUMS -print0 | xargs -0 md5sum >MD5SUMS

```
So if your cpro.txt is inside there as well, it's md5sum is also calculated. Open the MD5SUMS file in a text editor and see what it looks like.

Try checking the md5sums:
```

cd "/home/E/Documents/C_program"
md5sum -c MD5SUMS
# For testing, make a very small change in one of the source files; 
# add or remove a line or a space or something, and run the check again
md5sum -c MD5SUMS

```
The last check should alert you on that file now.

---

### Post by e24ohm on 2009-02-17
> **geirha said:**
> I don't quite understand what the purpose of that .txt-file is, but with the information given, doing the following will create /home/E/Documents/C_program/MD5SUMS with the md5sums of all files (in all subdirectories) of /home/E/Documents/C_program/:

```
cd "/home/E/Documents/C_program"
find -type f -not -name MD5SUMS -print0 | xargs -0 md5sum >MD5SUMS

```
So if your cpro.txt is inside there as well, it's md5sum is also calculated. Open the MD5SUMS file in a text editor and see what it looks like.

Try checking the md5sums:
```

cd "/home/E/Documents/C_program"
md5sum -c MD5SUMS
# For testing, make a very small change in one of the source files; 
# add or remove a line or a space or something, and run the check again
md5sum -c MD5SUMS

```
The last check should alert you on that file now.hey thanks for the insight, and yes i see that it works. This really helps me. I am not sure why the instrucutre wants us to do this, my guess it to learn how to use the md5sum commands.

thank you again.

I am not sure what all the switches, do...do you have a manuel or point me in the right place to find out this?

cheers!!!

---

### Post by geirha on 2009-02-17
If you wonder what a command does, always try "man *command*". In this case:
```
man md5sum
man find
```

---

### Post by e24ohm on 2009-02-17
> **geirha said:**
> If you wonder what a command does, always try "man *command*". In this case:
```
man md5sum
man find
```thank you very much, you have been so helpful and polite...thank you...

Cheers!!! Mate

---

### Post by biovore on 2009-02-17
You looking for the algorithm to do MD5SUMS ??
You trying to write a MD5SUM prorgam.  Or do you want to generate md5sums for the source files you have?

---

### Post by e24ohm on 2009-07-27
> **biovore said:**
> You looking for the algorithm to do MD5SUMS ??
You trying to write a MD5SUM prorgam.  Or do you want to generate md5sums for the source files you have?
I want to generate md5sums for the source files i have.

---


---
title: "Problems with PGP keys when attempting to get extra respositories"
date: 2005-04-12
forum: Desktop Environments
---

### Post by cajunaggie on 2005-04-12
I searched the forums this time but couldn't find the answer to this. I followed the "How to Get Extra Repositories" in the Unbuntu Guide and it went well up until the part with the PGP keys. When I run the command 
```
gpg --keyserver wwwkeys.eu.pgp.net --recv-keys 1F41B907
```
I get this:> 
gpg: error creating keyring `/home/jonathan/.gnupg/secring.gpg': Permission denied
gpg: keyblock resource `/home/jonathan/.gnupg/secring.gpg': file open error
gpg: error creating keyring `/home/jonathan/.gnupg/pubring.gpg': Permission denied
gpg: keyblock resource `/home/jonathan/.gnupg/pubring.gpg': file open error
gpg: no writable keyring found: eof
gpg: error reading `[stream]': general error
gpg: Total number processed: 0
Suggestions?

---

### Post by c_dog on 2005-04-12
Try 

```
sudo  gpg --keyserver wwwkeys.eu.pgp.net --recv-keys 1F41B907
```

---

### Post by joshmachine on 2005-04-12
[QUOTE=c_dog]Try 

```
sudo  gpg --keyserver wwwkeys.eu.pgp.net --recv-keys 1F41B907
```[/QUOTE]
 you shouldn't have to sudo this.   The ~/.gnupg folder contains your public and private keys for public key cryptography, and should be created and owned by the user not root.

first check that you can create any files in your home directory.  try 

$ touch /home/jonathan/empty.file

if this is true, and you haven't created any of these keys (you would know if you had)  try moving the existing ".gnupg" directory.

$ mv .gnupg .gnupg.old

then issue the command again.
I use gnupg, and if there is no existing keyring (where your keys are stored) it will create one.  

Cheers

---

### Post by cajunaggie on 2005-04-13
That fixed that problem but apparently this just isn't my week. I ran the next step
```
$ gpg --armor --export 1F41B907 | sudo apt-get key add- 
```
and got this:
> E: Invalid operation key
gpg: [stdout]: write error: Broken pipe
gpg: iobuf_flush failed on close: file write error

---

### Post by joshmachine on 2005-04-13
[QUOTE=cajunaggie]That fixed that problem but apparently this just isn't my week. I ran the next step
```
$ gpg --armor --export 1F41B907 | sudo apt-get key add- 
```
and got this:[/QUOTE]
 I think there is supposed to be a space between the "add" and the "-".

the dash tells apt to take the key from stdin (i.e in the pipe situation this is the output from the first command.

first try adding the space. Still not working?

then check if the gpg command is working try:

$ gpg --armor --export 1F41B907 

to ensure that portion is functioning correctly.  It should output an "armored" text version of the public key  (a big block of random looking characters)

you can save the output to a file by issuing a redirect command like so

$ gpg --armor --export 1F41B907 > key.pgp

of course you will have to have write access to the directory you do this in.

try to add the key not using piping.  To do this replace the "-" with the file name

$ apt-get key add key.pgp

Good Luck.

---

### Post by cajunaggie on 2005-04-13
Thanks

---

### Post by chaitatp on 2005-04-14
Friends, I've got some problems... Y_Y

I had a fresh installation of ``Hoary''.  Then I tried to install more packages with ``apt'' by 

``sudo apt-get update''

And the following is the output.

--------
chaitatp@taladnoi:~$ sudo apt-get update
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release.gpg [189B]             
Get:2 [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) hoary Release.gpg [189B]                    
Get:3 [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) hoary-updates Release.gpg [189B]
Hit [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) hoary Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release
Hit [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) hoary-updates Release   
Ign [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) hoary-updates Release 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Packages                    
Hit [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) hoary/main Packages                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Packages              
Hit [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) hoary/restricted Packages                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Sources                     
Hit [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) hoary/main Sources                            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Sources               
Hit [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) hoary/restricted Sources                      
Hit [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) hoary-updates/main Packages
Hit [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) hoary-updates/restricted Packages
Hit [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) hoary-updates/main Sources
Hit [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) hoary-updates/restricted Sources
Fetched 567B in 0s (791B/s)                              
Reading package lists... Done

W: GPG error: [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) hoary-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: You may want to run apt-get update to correct these problems

---------

T_T ... I then 

``sudo apt-get --allow-unauthenticated  update''

that I can install more packages using ``apt''.  But I think this is not the way the folks will do, eh?

Please advice me, thanks in advance.

---

### Post by chaitatp on 2005-04-14
Maybe I am a bit confusing.

 ``sudo apt-get --allow-unauthenticated  update'' 

didn't work.  I can't remember what I have done that made ``apt'' worked for a while.

---


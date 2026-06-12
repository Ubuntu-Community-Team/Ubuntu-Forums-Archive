---
title: "Run executable file from ftp"
date: 2009-06-07
forum: General Help
---

### Post by belaviyo on 2009-06-07
Hi

I have mounted a ftp drive from windows os in my ubuntu machine using this command: curlftpfs -o allow_other [ftp://192.168.11.1](ftp://192.168.11.1) windows/

The server allow me to create directory,..
but I cant run a executable file like this: ./my_exe where my_exe is on ftp folder (if I put this file in local drive then it can be executed), Is there any method to solve this problem?

Thanks

---

### Post by 3rdalbum on 2009-06-07
I'm not sure if what you're asking is possible.

I know next to nothing about FTP, but have you tried using chmod +x to give the file execute permission? Obviously you'd do it with the client, not on the Windows server :-)

---

### Post by JCoster on 2009-06-07
You probably already are but i just thought I'd check that you are attempting to run the EXE with WINE yes?  

If not then that's where you're going wrong.
```
sudo apt-get install wine
```

---

### Post by belaviyo on 2009-06-07
No I don't want to run a **windows executable**! I want to run for example a bash script, but this script is located on windows drives such as NTFS or Fat32 and I have access to it via curlftpfs as a local file in a virtual local folder (curlftpfs -o allow_other [ftp://192.168.11.1](ftp://192.168.11.1) windows/)

The problem is when we want to make a text file executable we need to chmod it to +x but in fat,NTFS,.. there aren't such attributes, My question is how can I run the script when it is hosted on windows drive?

P.S: assume that I cant copy the script into Linux local drive

---


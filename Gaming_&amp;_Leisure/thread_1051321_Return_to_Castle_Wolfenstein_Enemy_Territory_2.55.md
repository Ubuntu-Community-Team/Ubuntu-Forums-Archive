---
title: "Return to Castle Wolfenstein: Enemy Territory 2.55"
date: 2009-01-26
forum: Gaming &amp; Leisure
---

### Post by jstagame on 2009-01-26
can anyone help me where  to download the 
Return to Castle Wolfenstein: Enemy Territory 2.55  version for ubuntu please.Thaks in advance

---

### Post by Solarium on 2009-01-26
Hey jstagame,

I think you got a little confused with versions, first off here is the link: [http://returntocastlewolfenstein.filefront.com/file/Enemy_Territory;14408](http://returntocastlewolfenstein.filefront.com/file/Enemy_Territory;14408)

Secondly to mak things clear:
ET Version 2.55 is the standart game client(you get automaticly v2.55 when u download the client) and quite outdated and rarely used in servers.

The patch for it is ET v2.60 so mind want to get that as well if u plan server browsing and dont have a particular server in mind.

PS: you might wanna check out: [http://www.prime-squadron.com/](http://www.prime-squadron.com/) its a Return to Castle Wolfenstein: Enemy Territory gaming community we run 7 server with all kinds of mods, and i know we got more then few linux users who might be able to help in trouble shooting :P

---

### Post by jstagame on 2009-01-26
Solarium,Thank you very  much you,yeah your right kinda confuse here since i am new to linux hehe.thank you very much.

---

### Post by 3ventic on 2010-01-12
> **Solarium said:**
> Hey jstagame,

I think you got a little confused with versions, first off here is the link: [http://returntocastlewolfenstein.filefront.com/file/Enemy_Territory;14408](http://returntocastlewolfenstein.filefront.com/file/Enemy_Territory;14408)

Secondly to mak things clear:
ET Version 2.55 is the standart game client(you get automaticly v2.55 when u download the client) and quite outdated and rarely used in servers.

The patch for it is ET v2.60 so mind want to get that as well if u plan server browsing and dont have a particular server in mind.

PS: you might wanna check out: [http://www.prime-squadron.com/](http://www.prime-squadron.com/) its a Return to Castle Wolfenstein: Enemy Territory gaming community we run 7 server with all kinds of mods, and i know we got more then few linux users who might be able to help in trouble shooting :P
2.60 has more servers but less players.

2.55 has at least 3 times the player amount of 2.60. And the main reason is that there are 2.60 and 2.60b which confuse players even more. There is also 2.56 which I think is pretty forgotten.

---

### Post by ViperScull on 2010-01-12
The latest update of playdeb of 2.60b makes my game crash every time, and the sound doesnt work. It worked perfectly before that update

---

### Post by SuperPC on 2010-06-14
How do I install this?

---

### Post by ubun2ibun3 on 2010-07-10
After downloading the file, I'll assume into your Downloads folder, you will need to open the Terminal, where you should be presented with a console displaying:
```

sean@ubuntu:~$

```
where "sean" is replaced with whatever you have as your username, and "ubuntu" is replaced with whatever your system name is (it may also be ubuntu).  Like above, there should be a '~' character before the '$', which indicates you are in your home folder.  If not, you can simply type:
```

cd ~

```
which will take you to your home directory.

After doing so, you can type:
```

cd ./Downloads

```
which will take you to your Downloads folder, the default folder where your downloads from Firefox are stored.  If they are in a different folder, or a sub-folder within Downloads, you will need to enter the appropriate name, like if it were in the folder, Wolfenstein, within the folder, Downloads, you would type:
```

cd ./Downloads/Wolfenstein

```
Note that character case DOES matter!  In Linux, the folder "Downloads" is different from the folder "downloads".  Also notice the forward slash as compared to the backslash used in Windows.

After changing to the directory in which the file, et-linux-2.55.x86.run, was downloaded, it is necessary to change some attributes of the file in order for it to be executable.  Whereas in Windows, a file is considered executable or not executable based on its file extension, Linux operating systems do not make such an assumption.  It is necessary to 'tell' the system that it is an executable file.  In order to do this, type:
```

chmod +x ./et-2.55.x86.run

```
Which means to add the executable attribute to the file.  After doing so, because this is an installer that will need to write files to folders such as /usr/local/games, which are not owned by the normal user account, it is necessary to continue the installation process using permissions of the super user, which is done using the command:  sudo.
```

sudo ./et-2.55.x86.run

```
This will begin the installation process.  It is relatively self-explanitory.  It will ask for the folder into which it should be installed.  It would be best to leave this as the default values.  It will also ask if PunkBuster should be installed.  Unless you have any reason you do not want it, it is highly recommended to have it installed as most servers require it.

After the install, there should be an icon placed somewhere in your Applications tab.
Hope this was helpful!

---


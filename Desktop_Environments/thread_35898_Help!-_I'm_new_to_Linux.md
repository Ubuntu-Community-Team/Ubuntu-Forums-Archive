---
title: "Help!- I'm new to Linux"
date: 2005-05-20
forum: Desktop Environments
---

### Post by ChrisG on 2005-05-20
Hi, I'm new to linux (Which I just installed on my other computer) and it looks alot like DOS. I'm kind of stuck on what to do. When I first got it up, it said I had 1 new message. I didn't know what to do, but the message eventually went away, so I don't worry about it anymore. But anyways. I was wondering if anyone could give me a link to a website that is a complete guide / Tutorial to Ubuntu Linux. If anyone finds one please give me an email at [EMAIL=ChrisGray8923@aol.com]Chris Gray[/EMAIL]  ](*,)  [-X  \\:D/

---

### Post by sethmahoney on 2005-05-20
[QUOTE=ChrisG]Hi, I'm new to linux (Which I just installed on my other computer) and it looks alot like DOS. I'm kind of stuck on what to do. When I first got it up, it said I had 1 new message. I didn't know what to do, but the message eventually went away, so I don't worry about it anymore. But anyways. I was wondering if anyone could give me a link to a website that is a complete guide / Tutorial to Ubuntu Linux. If anyone finds one please give me an email at [EMAIL=ChrisGray8923@aol.com]Chris Gray[/EMAIL]  ](*,)  [-X  \\:D/[/QUOTE]
 To start off, try entering

```
startx
```

at the command prompt.  That should start the xserver, and after that things should look more familiar.

---

### Post by sethmahoney on 2005-05-20
Okay, here's the Ubuntu guide, which might not be what you have in mind, but it will be handy to have around:

[http://www.ubuntuguide.org/](http://www.ubuntuguide.org/)

and here is a list of commands to help you get through the whole command-line thing:

[http://www.reallylinux.com/docs/basic.shtml](http://www.reallylinux.com/docs/basic.shtml)

The weird thing is that Ubuntu should start the xserver automatically.  You shouldn't get the prompt when you boot up like that.  Anyone know how to fix that?

---

### Post by crazybill on 2005-05-22
I have a tutorial at [http://home.cvc.org/ac/learningUNIX.htm](http://home.cvc.org/ac/learningUNIX.htm) 

As for the new messages to which you refer, in a terminal write

 ```
$ **less /var/mail/username**
```  where "username" is your username.

Also, try roaming around this forum and going to 
[http://www.obuntuguide.com](http://www.obuntuguide.com)

---


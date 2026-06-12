---
title: "Having trouble with cp"
date: 2009-05-23
forum: General Help
---

### Post by PhilMize on 2009-05-23
Ok, I'm not very knowledgeable yet on the different commands in terminal to get things done. So I'm hoping you guys can shed some light on things for me.

I'm trying to copy and paste something from my desktop too a directory. I'm missing the command for telling cp the destination to paste too,

```
phil-laptop phil # sudo cp ~/phil/desktop/alsa-driver-1.0.20.tar.bz2
cp: missing destination file operand after `/root/phil/desktop/alsa-driver-1.0.20.tar.bz2'

```

So I guess my question is, what is the command I use to tell cp where to paste?

I want it to paste into /usr/src/alsa


help?

---

### Post by taurus on 2009-05-23
```
sudo cp ~/phil/desktop/alsa-driver-1.0.20.tar.bz2 /usr/src/alsa
```
Assuming there is a directory alsa in /usr/src.  Otherwise, alsa-driver-1.0.20.tar.bz2 will be name to alsa in /usr/src.

---

### Post by PhilMize on 2009-05-24
This is what I got...

> [IMG]http://www.flickr.com/photos/15759031@N02/3558908554/[/IMG]

---

### Post by Liolikas on 2009-05-24
> **PhilMize said:**
> This is what I got...
Empty quote?
If everything OK you will not get any response that is typical behavior of Unix like systems - print only errors and not spam: 
"oh keyboard is working" every 5 minutes like it should not work and something strange happened.

---

### Post by DeMus on 2009-05-24
> **PhilMize said:**
> Ok, I'm not very knowledgeable yet on the different commands in terminal to get things done. So I'm hoping you guys can shed some light on things for me.

I'm trying to copy and paste something from my desktop too a directory. I'm missing the command for telling cp the destination to paste too,

```
phil-laptop phil # sudo cp ~/phil/desktop/alsa-driver-1.0.20.tar.bz2
cp: missing destination file operand after `/root/phil/desktop/alsa-driver-1.0.20.tar.bz2'

```

So I guess my question is, what is the command I use to tell cp where to paste?

I want it to paste into /usr/src/alsa


help?

To copy something in terminal works differently from copying text in a file.
When you want to copy a file, files, or even complete folders you use the cp command as follows:

```
cp "original location/filename" destination
``` (without the quotes)

For more info type ```
man cp
```

---

### Post by PhilMize on 2009-05-24
> **Liolikas said:**
> Empty quote?
If everything OK you will not get any response that is typical behavior of Unix like systems - print only errors and not spam: 
"oh keyboard is working" every 5 minutes like it should not work and something strange happened.


Oops sorry about that, thats what i get for not checking my post.

> 
phil@phil-laptop ~ $ sudo cp ~/phil/desktop/alsa-driver-1.0.20.tar.bz2 /usr/src/alsa
cp: cannot stat `/home/phil/phil/desktop/alsa-driver-1.0.20.tar.bz2': No such file or directory

---

### Post by XCan on 2009-05-24
> **PhilMize said:**
> Oops sorry about that, thats what i get for not checking my post.

> phil@phil-laptop ~ $ sudo cp **~/phil/desktop/alsa-driver-1.0.20.tar.bz2** /usr/src/alsa
cp: cannot stat `**/home/phil/phil/desktop/alsa-driver-1.0.20.tar.bz2**': No such file or directory 

Are you sure the path is correct? Isn't the file alsa-driver-1.0.20.tar.bz2 in /home/phil/desktop/alsa-driver-1.0.20.tar.bz2? In the above you have /home/phil/phil instead of /home/phil. The tilde automatically puts you into your homefolder, i.e. /home/phil/.

---

### Post by taurus on 2009-05-24
> **XCan said:**
> Are you sure the path is correct? Isn't the file alsa-driver-1.0.20.tar.bz2 in /home/phil/desktop/alsa-driver-1.0.20.tar.bz2? In the above you have /home/phil/phil instead of /home/phil. The tilde automatically puts you into your homefolder, i.e. /home/phil/.

And besides, it's probably Desktop, not desktop since Linux/Unix is case SenSiTive.  ~/Desktop is not the same as ~/desktop.

---

### Post by boof1988 on 2009-05-24
Also...

Here are a couple more resources for CLI use.

This is a Ubuntu Community Page:

[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

Here is a forum thread (which has a link to a free download of Ubuntu Pocket Guide:

[http://ubuntuforums.org/showpost.php?p=6626411&postcount=1](http://ubuntuforums.org/showpost.php?p=6626411&postcount=1)

---

### Post by PhilMize on 2009-05-27
ok I got it, thanx for all your help guys!

What it ended up being was that like what Xcan said, my path was incorrect and hen like what taurus said the D needed to be capital.

This turned out to be the correct path
```
sudo cp ~/Desktop/alsa-driver-1.0.20.tar.bz2 /usr/src/alsa
```

---


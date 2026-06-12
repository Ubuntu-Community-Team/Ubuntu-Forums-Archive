---
title: "MSN Messenger sub?"
date: 2006-01-01
forum: General Help
---

### Post by s_spiff on 2006-01-01
Hey is there any substitues for Gaim and aMSN? I liked gaim, but it sometimes simple doesnt connect, as for aMSN, I didn't like its feel. Is there anything that I can use instead of these two?

---

### Post by oakz on 2006-01-01
kopete is a good IM client that supports MSN

---

### Post by s_spiff on 2006-01-01
but that works on KDE right? not GNOME?

---

### Post by earobinson on 2006-01-01
usualy if it starts with a k it is a kde app.

all kde apps will run on gnome and all gnome apps will run on kde. (you just need to install a lot of extra stuff to make them work)

---

### Post by JamesNorris on 2006-01-01
try amsn. It's what I use. [Website Here]("http://amsn.sf.net") They just released a new version, but the ubuntu packager took the source fro the wrong date so it's best to just compile from the source tarball they provide and download the ubuntu "human" skin seperately.

---

### Post by Lord Illidan on 2006-01-01
No need to compile from source. There is an ubuntu deb, too..

---

### Post by Sebby on 2006-01-01
I'm glad I've come across this thread.

I was also looking for an MSN replacement. Gaim just didn't do it for me, and though aMSN had the functionality, it looked awful. So, what would you say if it could look like the picture attached? ;)

---

### Post by Lord Illidan on 2006-01-01
The fonts are a damn sight better than mine. How did you get them that way?

---

### Post by Sebby on 2006-01-01
[QUOTE=Lord Illidan]The fonts are a damn sight better than mine. How did you get them that way?[/QUOTE]
It involves compiling aMSN with Tcl/Tk CVS. I did it a while ago 'manually', but Gandalf has since released a script that will do it all for you.

[http://www.ubuntuforums.org/showthread.php?t=102299](http://www.ubuntuforums.org/showthread.php?t=102299)

Let me know how you get on. Once installed, you can adjust the font size and make a bit smaller, then it should look great.

:cool:

---

### Post by JamesNorris on 2006-01-01
[QUOTE=Lord Illidan]No need to compile from source. There is an ubuntu deb, too..[/QUOTE]

Yes, but like I said, the ubuntu package isn't actually the correct date. It was a few days before the official 0.95 release.

The Current CVS version has a few little bugfixes, too.

---

### Post by s_spiff on 2006-01-01
[quote=Sebby]It involves compiling aMSN with Tcl/Tk CVS. I did it a while ago 'manually', but Gandalf has since released a script that will do it all for you.

[http://www.ubuntuforums.org/showthread.php?t=102299]("http://www.ubuntuforums.org/showthread.php?t=102299")

Let me know how you get on. Once installed, you can adjust the font size and make a bit smaller, then it should look great.

:cool:[/quote]
Hey Sebby, need some help here. New to linux, so please help me with installing the tarball and then also doing this scrip thing, whatever its called. I had downloaded firefox 1.5 too,, but when I installed it, I dunno what scrwed up, now browser started when i clickd on the icon, and since I didn't know how to correct it, I just reformatter the hdd, and reinstalled. So I don't wanna screw up again!:???:

---

### Post by Sebby on 2006-01-02
[QUOTE=s_spiff]Hey Sebby, need some help here. New to linux, so please help me with installing the tarball and then also doing this scrip thing, whatever its called. I had downloaded firefox 1.5 too,, but when I installed it, I dunno what scrwed up, now browser started when i clickd on the icon, and since I didn't know how to correct it, I just reformatter the hdd, and reinstalled. So I don't wanna screw up again!:???:[/QUOTE]
Don't worry about it - we've all been there. :)

There'e one problem and that is that Gandalf's website is down, but should be back today (I'm waiting too, so I'll post here when it's working).

When it is, this is what you have to do in a terminal:

```
cd /tmp
wget http://wael.nasreddine.com/files/ubuntu/easyamsn.tar.gz
tar xzvf easyamsn.tar.gz
cd easyamsn
sudo ./install
```

Gandalf's script should do the rest. :D

---

### Post by Sebby on 2006-01-02
Gandalf's site is now back up. Give it a try. :)

---

### Post by s_spiff on 2006-01-02
I Did what Sebby said, and then i got some loads of warnings when i did that ./install, and finally a pop up notice saying : aMSN has been installed in System Files ..or something of that sort. Is it ok?

---

### Post by Sebby on 2006-01-02
Well does it work? If not, post the error messages in this thread:

[http://www.ubuntuforums.org/showthread.php?t=102299](http://www.ubuntuforums.org/showthread.php?t=102299)

---

### Post by s_spiff on 2006-01-02
Also I went to aMSN home page, and there for downloads, there is no option for Ubuntu intel 86 series. I'm neither on a power pc or a 64 bit. What to do?

---

### Post by s_spiff on 2006-01-02
Sebby, what does that scrip exactly do? and no I don't think it worked. I mean I don't get any error, but the look and feel of the messenger hasn't changed one bit.

---

### Post by JamesNorris on 2006-01-02
[QUOTE=s_spiff]Also I went to aMSN home page, and there for downloads, there is no option for Ubuntu intel 86 series. I'm neither on a power pc or a 64 bit. What to do?[/QUOTE]

Try this one:
[Ubuntu x86]("http://prdownloads.sourceforge.net/amsn/amsn_0.95-3.ubuntu.deb")

---

### Post by s_spiff on 2006-01-02
thanks man.

---

### Post by s_spiff on 2006-01-02
I just downloaded that aMSN .deb package, what do I do now? How to install it?

---

### Post by Sebby on 2006-01-02
[QUOTE=s_spiff]I just downloaded that aMSN .deb package, what do I do now? How to install it?[/QUOTE]
Change to the directory where you downloaded the file to, then:

```
sudo dpkg -i amsn_0.95-3.ubuntu.deb
```

Don't expect a lot though - it won't look any different. You really need to use either the Easy aMSN script, or follow [this how-to](http://www.ubuntuforums.org/showthread.php?t=84765). The reason for this is that these 2 methods will use the latest Tcl/Tk, which will improve the look of the program somewhat.

Try Easy aMSN again first - delete the easyamsn folder from your home directory, then try again. If not, give the how-to a go - it's not too complicated.

---

### Post by JamesNorris on 2006-01-02
Why say that? aMSN have just abandoned tcl/tk 8.3 and don't fully support 8.5 yet, so using the latest tcl/tk is actually more likeky to cause problems.  Besides, the tcl/tk dev files that are in the ubuntu repos work perfectly fine here, and it looks OK to me. 

If using the officially sanctioned versions of the files works, why tell him to remove it and do it your way?

---

### Post by s_spiff on 2006-01-02
Hey, thanks sebby, everythings working now! but like you said, nothing much changed. Anyways thanks a lot for the help.  One problem still surfacing though, neither GAIM nor aMSN can connect to msn! GAIM does occasionally after a reboot, but otherwise uh uh... what can I say, my tough luck! Thank you.

---

### Post by Sebby on 2006-01-02
[QUOTE=JamesNorris]If using the officially sanctioned versions of the files works, why tell him to remove it and do it your way?[/QUOTE]
Because if you read his original post, you'll see that he doesn't like how Gaim functions, and he doesn't like the look of aMSN. And I just so happen to know a way of making aMSN look good, so I informed him. Is that okay with you? :rolleyes:

---

### Post by s_spiff on 2006-01-08
yup, and thanks to that way, amsn def. looks much better!

---

### Post by s_spiff on 2006-01-08
Any place where I can pick up more aMSN skins?

---


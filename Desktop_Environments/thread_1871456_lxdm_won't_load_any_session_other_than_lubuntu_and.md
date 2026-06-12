---
title: "lxdm won't load any session other than lubuntu and openbox"
date: 2011-10-28
forum: Desktop Environments
---

### Post by freaxtux on 2011-10-28
Hi all
I tried to install and use xubuntu-desktop after installing lubuntu, but lxdm doesn't load it.
I also tried loading lubuntu netbook session, but it also fails.
When I select the problematic sessions, type username and password, the password field disappears for a moment and it just asks username again.

thanks.

---

### Post by amjjawad on 2011-10-29
> **freaxtux said:**
> Hi all
I tried to install and use xubuntu-desktop after installing lubuntu, but lxdm doesn't load it.
I also tried loading lubuntu netbook session, but it also fails.
When I select the problematic sessions, type username and password, the password field disappears for a moment and it just asks username again.

thanks.

Hi :)

What release of Lubuntu do you have? how did you installed it?
You installed xbuntu-desktop package, right?

---

### Post by freaxtux on 2011-10-30
Oh, The Lubuntu is 11.10 version and was installed with USB. 
"Check disc for defects" menu didn't report any error.
Xubuntu-desktop is installed now. 
I tried to use LightDM but it also has problem so can't use that.
[http://ubuntuforums.org/showthread.php?t=1871466](http://ubuntuforums.org/showthread.php?t=1871466)

---

### Post by freaxtux on 2011-10-30
I just installed Lubuntu in my USB with Virtualbox (like installing on harddisk-I mounted iso file and USB on Virtual box) and there's also the problem so I guess it's not fault of installing procedure or my mishandling. It's running on the same computer and didn't tried on any other computer. My computer is VAIO VGN-FJ65L.

---

### Post by amjjawad on 2011-10-31
Have a look here: [http://ubuntuforums.org/showthread.php?t=1872303](http://ubuntuforums.org/showthread.php?t=1872303)

---

### Post by freaxtux on 2011-11-01
Well, I didn't ask how to install Lubuntu on USB. What I meant was that I could reproduce my problem again.

---

### Post by amjjawad on 2011-11-03
> **freaxtux said:**
> Well, I didn't ask how to install Lubuntu on USB. What I meant was that I could reproduce my problem again.

Ok, I got that :)
I'll try to search for similar issues and get back to you.
For faster assistance, you can visit our IRC Channel and the team will help you as well.

[Lubuntu One Stop Thread]("http://ubuntuforums.org/showthread.php?t=1844755") > Section B > [Contact us]("https://wiki.ubuntu.com/Lubuntu/ContactUs")

---

### Post by amjjawad on 2011-11-03
Did you check: **/usr/share/xsessions**?

For example: Lubuntu-Netbook.desktop
It has:


```
[Desktop Entry]
# The names/descriptions should really be better
Name=Lubuntu Netbook
Comment=Lubuntu Netbook - Lightweight X11 desktop environment based on LXDE
[B][COLOR="Red"]Exec=/usr/bin/startlubuntu-netbook
[/COLOR][/B]# Icon=
Type=Application
```

The line in red is very important.

Could you please check that?


I also found some useful info:

[http://manpages.ubuntu.com/manpages/lucid/man1/lxdm.1.html](http://manpages.ubuntu.com/manpages/lucid/man1/lxdm.1.html)

[https://help.ubuntu.com/community/Lubuntu/Documentation/FAQ/Workarounds#Lubuntu_Netbook_not_launching](https://help.ubuntu.com/community/Lubuntu/Documentation/FAQ/Workarounds#Lubuntu_Netbook_not_launching)

---

### Post by freaxtux on 2011-11-09
Sorry for late reply. I've been quite busy these days.

I guess the second link tells what was the problem.

I'm still a little busy, so I just removed the spaces for now.

I'll check it later and make a reply.

Thank you very much! :)

---

### Post by amjjawad on 2011-11-09
> **freaxtux said:**
> Sorry for late reply. I've been quite busy these days.

I guess the second link tells what was the problem.

I'm still a little busy, so I just removed the spaces for now.

I'll check it later and make a reply.

Thank you very much! :)

Most Welcome!
I'll be here so take your time ;)

---

### Post by gmargo on 2011-11-12
> **freaxtux said:**
> Hi all
I tried to install and use xubuntu-desktop after installing lubuntu, but lxdm doesn't load it.
I also tried loading lubuntu netbook session, but it also fails.
When I select the problematic sessions, type username and password, the password field disappears for a moment and it just asks username again.

thanks.

I have the same problem with **lxdm**.  It will start a Lubuntu desktop session, but I cannot get it to reliably start an Xfce4 session.

For the moment, I'm using the **slim** desktop manager.

---

### Post by amjjawad on 2011-11-12
> **gmargo said:**
> I have the same problem with **lxdm**.  It will start a Lubuntu desktop session, but I cannot get it to reliably start an Xfce4 session.

For the moment, I'm using the **slim** desktop manager.

Hi,

Have you checked the suggestions in this thread?

---

### Post by freaxtux on 2011-11-15
Thank you. It's works perfectly now.:D

---

### Post by gmargo on 2011-11-15
> **amjjawad said:**
> Have you checked the suggestions in this thread?

I finally working through everything and did some more testing.  The problem is caused by lxdm's "space in Name field" bug.  The workaround is to edit the /usr/share/xsessions/{xfce,xubuntu}.desktop files.

[https://bugs.launchpad.net/ubuntu/+source/lxdm/+bug/875991](https://bugs.launchpad.net/ubuntu/+source/lxdm/+bug/875991)

---

### Post by amjjawad on 2011-11-16
> **gmargo said:**
> I finally working through everything and did some more testing.  The problem is caused by lxdm's "space in Name field" bug.  The workaround is to edit the /usr/share/xsessions/{xfce,xubuntu}.desktop files.

[https://bugs.launchpad.net/ubuntu/+source/lxdm/+bug/875991](https://bugs.launchpad.net/ubuntu/+source/lxdm/+bug/875991)

That's very interesting to know and the one who reported that bug is one of the main developers in Lubuntu so definitely that must be on his to-do list :)

Thanks!

---

### Post by amjjawad on 2011-11-16
> **freaxtux said:**
> Thank you. It's works perfectly now.:D

Glad to know that but would you please do two things?

1- Post how exactly you managed to fix it
2- Mark your thread as SOLVED if you don't have further questions so that you will help others who run into similar issue :)

[IMG]http://ubuntuforums.org/picture.php?albumid=2161&pictureid=7263[/IMG]


Thank you!

---

### Post by freaxtux on 2011-11-16
> **amjjawad said:**
> Glad to know that but would you please do two things?

1- Post how exactly you managed to fix it
2- Mark your thread as SOLVED if you don't have further questions so that you will help others who run into similar issue :)

Thank you!

OK. In my case, sessions with spaces in their names caused the problem

1. Open /usr/share/xsessions with superuser permission
(Alt+F2 - gksu pcmanfm /usr/share/xsessions)

2. You'll see files with name of sessions. _Renaming the files won't do_. Open the one you have problem with leafpad. _Don't doubleclick on it._
(Right click - Leafpad. if you don't see leafpad, select "Open with..."and search for it)

3. Find "Name=<<session name>>" and delete any space, or you can replace it with dash or whatever you want.

4. As I'm Korean user, I also edited "Name[ko]=<<session name>>" part. I think editing only the name of your language will do, but I edited both. Rest parts of the file don't matter. Wide characters(non-alphabetic characters. &#54620;&#44544;(*Han-geul*) worked, at least.) don't matter. Just delete space of the name of your locale.

That's all. Now you will be able to log in to the session.;)

---

### Post by todonormal on 2012-04-20
Great. I need to disable GNOME/Openbox, KDE/OpenBox, Lubuntu Netbook, LXDE and Openbox options. And enable only Lubuntu 

Very easy. 
sudo leafpad *desktopsession*.desktop
I change options
#exec
#Tryexec
:guitar:

Thanks for advanced

---


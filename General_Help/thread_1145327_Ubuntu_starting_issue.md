---
title: "Ubuntu starting issue"
date: 2009-05-01
forum: General Help
---

### Post by Squinchy on 2009-05-01
I'm having problems with starting Ubuntu after i installed it, the OS starts great right after the installation but if a restart or power down the OS wont start

Here is a video of what happens when i restart:
[http://www.youtube.com/watch?v=r3tga3z_beM](http://www.youtube.com/watch?v=r3tga3z_beM)

Any ideas what this might be ?

Thanks in advance.

---

### Post by drs305 on 2009-05-01
As you get the grub menu counting down, hit ESC. If you have a recovery option available, select that and then the "Fix X" option to see if that solves things. That's probalby the easiest thing to try as a first step.

---

### Post by Legace on 2009-05-01
Do you have a ATi grpahics card?
Did you install the FGLRX grpahics driver?

---

### Post by Squinchy on 2009-05-01
Ok i will try to hit Esc and access the Fix x

Yes it's a ATi grpahics card

I did install
ATI binary x.org driver
And
ATI Catalyst control center
in the Add/Remove Applications
[IMG]http://pic60.picturetrail.com/VOL1731/12315575/21907249/363079305.jpg[/IMG]

Oh yes and the pc is a IBM T43  2668-F7G

---

### Post by Squinchy on 2009-05-01
Well Fix x did not have any effect

Any more ideas how to fix this ?

---

### Post by Squinchy on 2009-05-02
Any one ?

Really want Ubuntu to work on my pc sins windows sucks and i don't like Kubuntu as much as Ubuntu

---

### Post by delcypher on 2009-05-02
It looks like a driver issue. 

You could find out what's happening by looking the X.org log file. In recovery mode in the root shell prompt you can type.

```
less /var/log/Xorg.0.log
```

Press h to get a list of the keycombinations you can use to scroll through the log (IT'S BIG) and see if there are any error messages (to go to the very end press G (make sure it's capital)).

You could try regenerating your xorg.conf file using the aticonfig utility. 

Start ubuntu in recovery mode and "Drop to root shell prompt" and type

```
aticonfig --initial --ovt opengl
```

Then reboot (type reboot) and try booting as normal.

If that doesn't work you could try using the Xorg program to reconfigure your xorg.conf.

In the root shell (as before) type:

```
Xorg -configure
```

That should create a Xorg.conf.new file in the directory you are in (probably the root home directory - /root). 

Now we will make a backup of the current Xorg.conf file and put the new Xorg.conf file in the /etc/X11 directory.

```
mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
cp xorg.conf.new /etc/X11/xorg.conf

```

Now reboot and see if that works.

Sorry if I can't be of anymore help.

---

### Post by Squinchy on 2009-05-02
Yeah i guess it was the ATI binary x.org driver And ATI Catalyst control center

I reinstalled Ubuntu, updated but did not install the ATI drivers, now i can turn off the computer and start it up just fine :)

---


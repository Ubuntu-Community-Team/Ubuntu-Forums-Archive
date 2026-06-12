---
title: "Need help installing Humble Indie Bundle games"
date: 2010-12-25
forum: Gaming &amp; Leisure
---

### Post by lightningfox on 2010-12-25
I am running Ubuntu 10.10 64 bit GNOME.

Today I bought the Humble Indie Bundle  [http://www.humblebundle.com/](http://www.humblebundle.com/)


Most of the games have .deb files but some only have .sh or .bin


Lugaru only has .bin

I downloaded Lugaru's .bin file and made it executable.

Then from terminal I did:   ./lugarufilename.deb


I got this error message:

```
/usr/lib/gio/modules/libgvfsdbus.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgvfsdbus.so

```

I'm not sure what the error message means.

Please help me install Lugaru.

---

### Post by clayton2 on 2010-12-25
Put the .bin in your home folder.

Then run these commands, assuming you left the Lugaru filename the way it was originally:
```
chmod +x lugaru-full-linux-x86-1.0c.bin
./lugaru-full-linux-x86-1.0c.bin
```

---

### Post by lightningfox on 2010-12-25
Thank you but I had already made the file executable before starting this thread.

Please help me to install Lugaru.

---

### Post by nerdy_kid on 2010-12-25
> **clayton2 said:**
> Put the .bin in your home folder.

Then run these commands, assuming you left the Lugaru filename the way it was originally:
```
chmod +x lugaru-full-linux-x86-1.0c.bin
**./lugaru-full-linux-x86-1.0c.bin**
```

run both commands clayton2 said should do it

---

### Post by OgreProgrammer on 2010-12-26
> **lightningfox said:**
> I am running Ubuntu 10.10 64 bit GNOME.

Today I bought the Humble Indie Bundle  [http://www.humblebundle.com/](http://www.humblebundle.com/)


Most of the games have .deb files but some only have .sh or .bin


Lugaru only has .bin

I downloaded Lugaru's .bin file and made it executable.

Then from terminal I did:   ./lugarufilename.deb


I got this error message:

```
/usr/lib/gio/modules/libgvfsdbus.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgvfsdbus.so

```I'm not sure what the error message means.

Please help me install Lugaru.

wrong ELF class means you are trying to use a 32 bit game with a 64 bit system. In synaptic look for the ia32 libs package and install it. This will enable compatibility libraries. Then run ./lugarufilename.bin again.

---

### Post by Spr0k3t on 2010-12-26
```
sudo apt-get install ia32-libs
./lugaru-full-linux-x86-1.0c.bin
```

That should get you installed and working fine.

---

### Post by lightningfox on 2010-12-28
Hi

I did all of what you said.

The terminal still shows the same error message, but I got an installation window and I installed Lugaru and the installation seemed to be fine.

Lugaru appeared in Applications>Games menu.

I played it a little and it seemed to run fine.

I don't know why I still got the error messages when I ran the Lugaru installer from the terminal. Does it matter if I got those messages?

---

### Post by ivarn on 2010-12-29
You know lugaru is a free game you can also find in the synaptic, right?
Well, now you do.

---

### Post by TurtleKing on 2011-01-17
> **clayton2 said:**
> Put the .bin in your home folder.

Then run these commands, assuming you left the Lugaru filename the way it was originally:
```
chmod +x lugaru-full-linux-x86-1.0c.bin
./lugaru-full-linux-x86-1.0c.bin
```
Thank You. I had to re-download it again, but after following your instruction without messing with the file at all it went through and installed. Good thing I decided to wait to the game installed before I deleted the email with the code.:P

---

### Post by CoreyB. on 2011-01-17
[deleted by user]

---

### Post by clayton2 on 2011-01-17
> **TurtleKing said:**
> Thank You. I had to re-download it again, but after following your instruction without messing with the file at all it went through and installed. Good thing I decided to wait to the game installed before I deleted the email with the code.:P

I would keep that link to that download page for a couple reasons:

1. You need to re-install your Linux machine, and you didn't save a local copy of the installers.

2. You get a Windows or Mac machine and would like to play those games on those machines.

3. The games could be updated.  For example, they are looking to put the latest version of Gish on there, plus, Cortex Command and Revenge of the Titans are still in beta and without-a-doubt will be updated.

---

### Post by R33D3M33R on 2011-01-17
> **clayton2 said:**
> I would keep that link to that download page for a couple reasons:

1. You need to re-install your Linux machine, and you didn't save a local copy of the installers.

2. You get a Windows or Mac machine and would like to play those games on those machines.

3. The games could be updated.  For example, they are looking to put the latest version of Gish on there, plus, Cortex Command and Revenge of the Titans are still in beta and without-a-doubt will be updated.

You can always have your code resent to your e-mail address. Check the humblebundle page.

---

### Post by clayton2 on 2011-01-17
> **R33D3M33R said:**
> You can always have your code resent to your e-mail address. Check the humblebundle page.

 [FONT=Verdana]Touché, but it certainly isn't a hassle to just leave the Humble Bundle e-mail floating in your inbox.[/FONT]

---

### Post by clayton2 on 2011-01-17
[double post][FONT=Verdana][/FONT]

---

### Post by TurtleKing on 2011-02-19
Sorry for the late reply, I actually left the email as you mentioned is not much of inconvenience to delete it. I can't wait for Lugaru 2 also known as Overgrowth. Multi-player 3rd person view fighting game? I can totally see me and another player just diving into a group of 30 wolves with crazy combos.:p

---


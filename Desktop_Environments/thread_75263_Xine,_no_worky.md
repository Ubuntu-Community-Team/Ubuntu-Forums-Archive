---
title: "Xine, no worky"
date: 2005-10-13
forum: Desktop Environments
---

### Post by Haiyadragon on 2005-10-13
I installed Kaffeine-xine and Amarok-xine but both won't play anything. At least, Kaffeine won't play avis and Amarok won't play mp3s. They don't give me any errors they just sit there.

I really like my media files fast and synced and all so I would prefer not using gstreamer. Any help with this would be appreciated.

---

### Post by DJ_Max on 2005-10-13
Did you install the suggested and recommended packages? From what I've seen the Xine packages will not install a lot of codecs you're looking for.

```
apt-cache show libxine1
```
It will show packages it suggest. Such as *libmad0*. There's also *ffmpeg*. Try looking through these forums for others.

---

### Post by Haiyadragon on 2005-10-14
Ok, thanks. Installing libmad0 and ffmpeg did it. I thought they were dependencies and didn't care to check. Thanks!

---

### Post by meborc on 2005-10-14
ok, i have a different problem with xine... it works just fine when i insert a dvd... sound, picture... everything is OK... but when i open the menu, to open files in my comp, the menu font is very strange.. small and barely readable... i choose a movie i want to see, and it just closes... nothing happends... no error mess... just close :confused: 

EDIT: just tried my mplayer... same thing... can someone help? :(

---

### Post by sala on 2005-10-14
I got also problem with xine. When i select some media file to play with xine then xine just quit's without saing nothing
```
sala@redbox:~$ xine
This is xine (X11 gui) - a free video player v0.99.3.
(c) 2000-2004 The xine Team.
xiTK received SIGSEGV signal, RIP.
Aborted
```
I also got the same error with ubuntu 5.10 preview release

---

### Post by sala on 2005-10-15
[QUOTE=sala]I got also problem with xine. When i select some media file to play with xine then xine just quit's without saing nothing
```
sala@redbox:~$ xine
This is xine (X11 gui) - a free video player v0.99.3.
(c) 2000-2004 The xine Team.
xiTK received SIGSEGV signal, RIP.
Aborted
```
I also got the same error with ubuntu 5.10 preview release[/QUOTE]
Some ideas? anyone?:(

---

### Post by DJ_Max on 2005-10-15
I jus upgraded to Breezy, and the new Xine version is 1.0.1, and it's called *libxine1c2*. This replaces libxine1.

---

### Post by mentrei on 2005-10-19
I Had the same problem, amarok and kaffeine don't play any sound, even when i installed all the codecs and libraries. But i installed the libmad0 suggested by dj, and everything works fine! Thanks a lot.
PS: Sorry for my bad english (i'm from brazil):D 
PS2: I use Ubuntu 5.10.

---

### Post by erbogasto on 2005-10-21
I got a similar problem too with xine :
I've installed xine-ui,gxine and totem-xine(from universe/multiverse repos) with all the codecs (I had them perfectly working on Hoary), and they perfectly work (divx,mp3,dvd ecc.) only if I'm on line (in internet) .
I use a dsl ethernet modem connection (pay for minute) so when I need connection $pon dsl-provider $poff (eth0 is automatically configured by dhcp with dynamic adress at boot-time) .
If I launch xine-ui gxine ... not on line they crash just after the bootsplah .
By comman-line the result is :

chicco@ubuntubox:~$ gxine
ERROR: Could not determine network interfaces, you must use a interfaces config line
chicco@ubuntubox:~$ xine
Questo &#195;&#168; Xine (X11 gui) - un riproduttore video libero v0.99.3.
(c) 2000-2004 Il team di Xine.
chicco@ubuntubox:~$ totem

(totem:9447): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

(totem:9447): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed
ERROR: Could not determine network interfaces, you must use a interfaces config line

Where do I have to put this "interfaces config line" ?
I've tried reinstalling, purging,reconfiguring,on-line and not on line, but the result is the same libxine needs a "interfaces config line" !!!

Can someone help me please ?
Ciao Andrea from Italy  :D

---

### Post by erbogasto on 2005-11-22
Hi everibody,I solved the problem, may be this helps someone else...
I simply changed my ip address from dynamic with dhcp ,to static ip address, and everything goes right its way.(I think there is a little bug in all this but don't really know where...)
Bye Andrea :D :D :D

---


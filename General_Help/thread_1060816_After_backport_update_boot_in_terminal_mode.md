---
title: "After backport update boot in terminal mode"
date: 2009-02-05
forum: General Help
---

### Post by Hippy Tesla on 2009-02-05
I have downloaded some backport updates an hour ago and since then, I cannot start X. Ubuntu boots in terminal mode. Any way to Undo those updates? I have edite sources list using live CD, but I need to uninstall those updates and I don't know their names.

I have also installed Quake III Arena in the same session, but I doubt that could make a problem.

Thanks in advance.

EDIT: Tried startx, but X seems to fail. Any logs I need to dump here so someone caould help?

---

### Post by kthakore on 2009-02-05
Please show the output for the following:

```

 echo -e "State \tLast change \t \tName" > PkgLog && ls -lsrt /var/lib/dpkg/info/*.list | awk '{print $6"\t"$7" "$8"\t"$9}' | sed -e "s/\/var\/lib\/dpkg\/info\///" -e "s/.list//" -e "s/^0\t/Removed \t/" -e "s/^[0-9]*\t/Installed\t/"

```

This should give you a long chronological list of date and package name. The new ones are at the end of the command. Copy out all the install for the start of the time u installed them. If u cannot remember the exact time post the entire day's log.

In the meantime u can run 
```

sudo apt-get install -f 

```
to see if there are any mid install packages.

---

### Post by Hippy Tesla on 2009-02-05
Wait, all this at once, or these are more then one command lines? I'm rebooting to Ubuntu now to try.

---

### Post by kthakore on 2009-02-05
The first one tells you all the packages you have installed. At the end of the list is the packages u have installed recently. I need to know hat u installed to see if they affect X. Just copy the whole line and paste it in the command line. The second command do it after you post all the packages u have installed on the day you broke X.

---

### Post by Hippy Tesla on 2009-02-05
I cannot start any GUI program. Firefox too. I used Windows for posting first two posts, now I'm using Live CD. I got the lis. Programs installed during that session in chronological order:

```
quake3-data
liblircclient
gimp-data
libgimp2.0
brasero
libbrasero
```I uninstalled them all except Q3A using sudo apt-get remove PROGRAM NAME. All of these were backport updates I enabled while I was trying to enable repository for Quake II.

Now, after uninstall, when I try to start X (sudo startx ot just startx) the last line is different:

```
xauth: error in locking authority file /home/tesla/Xauthority
```It tries to start X, but returns to terminal mode. I really appreciate your help, because all my wokr is trapped there.

I can access my files and configfiles from Live Session, so maybe I can change something from here?

EDIT: After installation of Q3A, it's Point Release is hanging in /root: linuxq3apoint-1.32b-3.x86.run
Should I delete it or something?

---

### Post by Hippy Tesla on 2009-02-05
I have tried to start Gnome Display Manager, and it returns this:
```
gdm: Symbol lookup error: /usr/lib/libgio-2.0so.0: undefined symbol: g-thread-gettime
```
and fails. Anything I can do from Live Session, Aptitude UI or terminal mode? In terminal mode, networking is not working. Anything I can do like "System Restore" for Windows? Installation repair?

---

### Post by redilyn on 2009-02-05
First ensure that gdm isn't running

```

sudo killall gdm

```

When in the terminal type the following

```

ls -a /home/telsa

```

Look for and delete any files in /home/telsa/ that start with .Xauthority

```

sudo rm /home/telsa/.Xauthority

```

Then try to start gdm again

```

startx

```

---

### Post by Hippy Tesla on 2009-02-07
There was no Xauthority, I've tried everything until 4AM, then reinstalled Intrepid after learning how to backup all packages and settings and it works perfectly now. Thanks guys, shut this down now.

---

### Post by Tendie on 2009-03-18
I had same problem after the following on lenovo W500:

1. It had vista pre-installed (supports switchable graphics)
2. I downgraded to xp (doesn't support switchable graphics)
3. Then I installed my main OS, Ubuntu. But i made a blunder coz I installed ubuntu 8.04.2. The laptop is fairly modern so it needed the latest kernel for the intel wireless card to work (there were other options but I am not experienced).
4. So I upraded to 8.10.
5. Unfortunately, Ubuntu doesn't support switchable graphics either.

Coz of problem (According to me):
((IF U GOT A SWITCHABLE GRAPHICS CARD SYSTEM))

It appears the BIOS Display information sets to 'switchable graphics' by default on booting, then our dear Linux can not handle the conflict because it sees both graphic cards and cant manage them (yet).

Solution:

( on W500: F1 on booting to enter BIOS>>Configure>>change 'switchable graphics' to 'descrete graphics' or the other less powerfull one if you wish - m not sure about path and dont want to reboot to check - sorry). Save and exit and you will be happy.

Way forward:

Please, experienced guys, may yyou provide us with better option. Its not standard to be tempering with the BIOS on evry boot.

Good day.

---


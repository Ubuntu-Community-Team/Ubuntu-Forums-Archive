---
title: "Updates broke unity"
date: 2013-02-20
forum: Desktop Environments
---

### Post by blackangelpr on 2013-02-20
Greetings i just made the updates and had broke unity the only way i can access a browser is by right click on the screen change back ground go back to setting click on ubuntu one and magane other decives so it actually opens a browser window ... long work around before the update everything was perfect... any thought of how can i get my machine back?   


thanks in advance):P

---

### Post by fuorviatos on 2013-02-20
Hello :)

What you mean by "browser". Is that the web one or the file manager?
Also, that'd would be nice to know what have you updated in your system.
Can you show us last records of your apt.log?

---

### Post by blackangelpr on 2013-02-20
Sorry for the little information I was unable to do lots of thing I write now from my iPad :( can't open anything now at the laptop except for the terminal



Here is some sys information
Asus g73jh
Ubuntu 12.10  X64
After installing today's updates it request a restart then when logged in unity did not show I try to restart it and says:



Compiz (core) - error: plugin initscreen failed: unityshell
Compiz (core) - error: failed to start plugin: unityshell
Compiz (core) - info: unloading plugin: unityshell


X error of request: badwindow (invalid window parameter)


Major opcode of failed request: 18 (x_changeproperty)
Resource Id in failed request: 0xe00005
Serial number failed request: 8279






Hope this help please let me know if anything else is need it that I can type on the tablet xd

---

### Post by blackangelpr on 2013-02-20
Had try this in the past and  did work but not now :   sudo apt-get install linux-headers-$(uname -r)

Currently trying this: [http://askubuntu.com/questions/206228/compiz-has-broken-after-installing-12-10-with-ati-catalyst-12-10-drivers](http://askubuntu.com/questions/206228/compiz-has-broken-after-installing-12-10-with-ati-catalyst-12-10-drivers)

This  did not work as well

---

### Post by fuorviatos on 2013-02-20
OK. I can see you're trying to install a new kernel. Well, don't do it because we need extra info to understand if your problem is related to it or not (I have doubts it is)
I need to see what packages you've installed to your system to understand what may have gone wrong, so, when you have the chance to work again on your laptop shell, type in the following command and paste here the output (use the wrap function)

> sudo tail -n 30 /var/log/dpkg.log

---

### Post by blackangelpr on 2013-02-20
Added a picture since cant get startx to work now :(

---

### Post by fuorviatos on 2013-02-20
Try to boot and hold the shift button to get to the grub menu, then choose the line with a different kernel.

---

### Post by blackangelpr on 2013-02-20
Do not work it goes directly to tty1

---

### Post by fuorviatos on 2013-02-20
Try to follow those steps [http://askubuntu.com/a/88420](http://askubuntu.com/a/88420) to activate the menu.

---

### Post by ahernp on 2013-02-21
I've just had the same problem. Things were working fine until I applied today's kernel update. After the restart the Unity launcher panel and window decorations had disappeared.

As suggested above, I installed the latest linux headers (in this case linux-headers-3.5.0-24-generic).

After another restart Unity was working normally again.

---

### Post by fuorviatos on 2013-02-21
> **ahernp said:**
> I've just had the same problem. Things were working fine until I applied today's kernel update. After the restart the Unity launcher panel and window decorations had disappeared.

As suggested above, I installed the latest linux headers (in this case linux-headers-3.5.0-24-generic).

After another restart Unity was working normally again.
@blackangelpr - Can you try if this does the trick for you and if so, mark the thread as solved?

---

### Post by tadis on 2013-02-21
> **ahernp said:**
> I've just had the same problem. Things were working fine until I applied today's kernel update. After the restart the Unity launcher panel and window decorations had disappeared.


Same thing to me too.
Kernel is the newest one.

---

### Post by fuorviatos on 2013-02-21
Any bug reports on Launchpad for this yet?

---

### Post by tadis on 2013-02-21
Fixed by reinstalling ubuntu-desktop:

```
sudo apt-get install --reinstall ubuntu-desktop
```

---

### Post by fuorviatos on 2013-02-21
@tadis - mark this thread as SOLVED please.

---

### Post by blackangelpr on 2013-02-21
The problem: 
[INDENT]After the latest update for ubuntu 12.10 the system crash unity[/INDENT]

The solution?:
[LIST=1]
[*]sudo restart unity  //This did not work
[/LIST]

Then found out the update broke the ati proprietary drivers

Then I proceeded to do the following to fix the :evil:(-_-) error:

1) sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev*

since was unable to delete all of it i force it
2) sudo sh /usr/share/ati/fglrx-uninstall.sh --force

Great i can boot again but,, cant log in to my admin account ~~
so the guest mode enters and again no unity :-({|=

3) sudo apt-get -f install ubuntu-desktop

reboot again

](*,) and no unity no admin account ....

guys what i am doing wrong ?? LOL 

i am not an expert just in case  so please be kind XD XD i am still learning thank in advance.. [-o<

will need to re-do the xorg file again?

---

### Post by blackangelpr on 2013-02-21
found out i do not have a xorg.conf back up to restore it ,,, any ways to make the computer make one or download the latest one?](*,)  sorry for all the questions XD

---

### Post by blackangelpr on 2013-02-21
> **blackangelpr said:**
> found out i do not have a xorg.conf back up to restore it ,,, any ways to make the computer make one or download the latest one?](*,)  sorry for all the questions XD

copied the original xorg.conf to the field 

maked a new user name to test ..after getting in same thing unity do not work ? :X

---

### Post by blackangelpr on 2013-02-23
Got tired since i do not have time to play around i got back to 12.04 already submitted some bugs before on 12.10 so at least i helped XD good luck and thanks anyway for the helping hand ):P

---


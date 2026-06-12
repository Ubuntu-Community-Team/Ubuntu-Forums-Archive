---
title: "Changing hostname messes up system"
date: 2006-08-03
forum: Desktop Environments
---

### Post by ralphmerridew on 2006-08-03
I didn't like the hostname I chose when initially creating the system, so I decided to change it.

sudo hostname _______
(and possibly wait a bit for it to forget you recently sudoed)

Now 
- sudo won't run because it can't gethostbyname the new name
- I can't open any new windows under X
though I can continue running any programs started beforehand.

Any tips on how to unhose my system?

---

### Post by ralphmerridew on 2006-08-03
Any ideas?

---

### Post by Ramses de Norre on 2006-08-03
Do sudo hostname and set the old name back? Then you can set a new one in /etc/hostname.

---

### Post by ralphmerridew on 2006-08-03
**sudo won't run because it can't gethostbyname the new name**

---

### Post by fragos on 2006-08-03
System-> Adminstration-> Networking-> General tab

---

### Post by christhemonkey on 2006-08-03
Boot up into recovery mode and then type:
```
hostname ____ 
```

To get into recovery mode, press 'esc' whilst booting to get into the GRUB menu, and then select recovery mode.
Eventually it will dump you at a root terminal.

---

### Post by butchd on 2006-08-03
FYI in my 6.06 there is no "networking" in that menu list, only "network tools." Why is it hidden?

---

### Post by ralphmerridew on 2006-08-03
> **fragos said:**
> System-> Adminstration-> Networking-> General tab

If I try to do that, it spins a bit but doesn't put up the new window.  (Probably related to the fact that I can't start any new X programs.)

---

### Post by cantormath on 2006-08-07
> **ralphmerridew said:**
> If I try to do that, it spins a bit but doesn't put up the new window.  (Probably related to the fact that I can't start any new X programs.)

press
```
<ctrl>+<alt>+F1
```
or F2 etc.

login 

```
sudo nano /etc/hostname,
```

nano is a text editor, if you dont have it, get it or use vi.

delete whatever is there, if anything, and type your hostname
ie
```
cantormath-laptop
```

then press
```
<ctrl>+x
```
to exit, type y to save and hit enter, cause you dont want to change the name of what file it saves to. hostname should already be typed in there.

added: if you are changing the hostname to something new, after you change  and save /etc/hostname, open /etc/hosts:

```
sudo gedit /etc/hosts
```
```

127.0.0.1 localhost 
127.0.1.1 <OLDHOSTNAME>
```

change the old hostname to the new hostname next to 127.0.1.1, save and reboot.

it should fix the problem...

if you have to use vi
```
<ctrl>+<alt>+F1
```
```
sudo vi /etc/hostname
```
hit the letter i, delete whatever is there, and type the hostname you want to use.
then type <esc>
then type <:> (and im mean <SHIFT>+<;>)
type wq (which means write and quit)
and reboot

added: again if hostname is new, change /etc/hosts file to have new hostname next to 127.0.1.1
```
sudo reboot 
```

lol, I just did that to myself..

---

### Post by fdoving on 2006-08-07
It is a good idea to change all instances of the old hostname in /etc/hosts to the new, when changing the hostname.

That way gethostbyname will succeed.

- Frode

---

### Post by cantormath on 2006-08-07
> **fdoving said:**
> It is a good idea to change all instances of the old hostname in /etc/hosts to the new, when changing the hostname.

That way gethostbyname will succeed.

- Frode
I changed it thanx....

---


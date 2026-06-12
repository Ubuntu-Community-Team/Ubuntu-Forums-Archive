---
title: "UT2004 Error"
date: 2008-06-27
forum: Gaming &amp; Leisure
---

### Post by Harkainos on 2008-06-27
I have searched through the forums to no avail. I have followed the how to and the game appears to be installed. 

When I click the icon, nothing noticeable happens, so I try it in Terminal and here is what I get:

[COLOR="YellowGreen"]nick@Compy386:/usr/local/games/ut2004$ ut2004
./ut2004-bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory[/COLOR]


Now, I have gone to my /home folder and checked for the ./ut2004-bin directory and it isn't listed there, in GUI or in Terminal (ls -la)

How do I get this to work? Because that directory isn't there, I cannot post UT2004.log - because that is where it would be, wouldn't it?

I am running Hardy and Installed from the DVD. I didn't patch anything (at a loss for that, I'll research that).

---

### Post by Cappy on 2008-06-27
For 32-bit Ubuntu Hardy:
```
sudo apt-get install libstdc++5
```

For 64-bit Ubuntu Hardy:
```
sudo apt-get install ia32-libs
```

You can use synaptic to install those packages, if you prefer.

---

### Post by Cresho on 2008-06-28
dont worry, its easy getting this puppy running, do as the above guy said.

---

### Post by eragon100 on 2008-06-28
I installed the editor's choice edition yesterday evening, and since then, everytime I click on "join game" or "community" in the main menu, I can't connect to the master server. Is it down? :(

---

### Post by Cresho on 2008-06-28
you patched it up?

---

### Post by Harkainos on 2008-06-28
Wow, that fix was easy.

How do I go about patching the game?

---

### Post by Drakkor on 2008-08-26
I'm getting this error,but the game runs,but the display is wacked
drakkor@drakkor-desktop:~$ sudo ut2004
[sudo] password for drakkor: 
WARNING: ALC_EXT_capture is subject to change!
Xlib:  extension "XiG-SUNDRY-NONSTANDARD" missing on display ":0.0". :(

---

### Post by Perfect Storm on 2008-08-26
First (a good advise), never run with sudo, you're compromising your security.

Are you running 32 or 64bit? Which video card do you have? is the driver installed?

---

### Post by Drakkor on 2008-08-26
It's a 32bit
00:10.0 VGA compatible controller: nVidia Corporation GeForce 7100/nForce 630i (rev a2)
and I have

---

### Post by Perfect Storm on 2008-08-26
What about other 3D games?

---

### Post by Drakkor on 2008-08-26
I just clean installed Hardy,and don't have any other 3D games

---


---
title: "Online Bomberman"
date: 2007-04-09
forum: Gaming &amp; Leisure
---

### Post by moot on 2007-04-09
Is there anyway to get Online Bomberman to run under Wine?

[http://www.broomop.com/Bomberman/news.php](http://www.broomop.com/Bomberman/news.php)

---

### Post by david_kt on 2007-04-09
> **moot said:**
> Is there anyway to get Online Bomberman to run under Wine?

[http://www.broomop.com/Bomberman/news.php](http://www.broomop.com/Bomberman/news.php)

Yes, just try it. If it have error, download mfc42.dlll and syswin.dll from internet and out it on:

```
/.wine/drive_c/windows/system32
```

And set the dlloverrides for launch.exe for those 2 dlls to native,builtin. I have not tried myself though as it need to have username and password, but I don't play this game.

DK

---

### Post by moot on 2007-04-09
> **david_kt said:**
> Yes, just try it. If it have error, download mfc42.dlll and syswin.dll from internet and out it on:

```
/.wine/drive_c/windows/system32
```

And set the dlloverrides for launch.exe for those 2 dlls to native,builtin. I have not tried myself though as it need to have username and password, but I don't play this game.

DK

I downloaded mfc42.dll and put it there, out syswin.dll there, and ran the game from:

```
~/.wine/drive_c/Program Files/BMO
```


Using the terminal command:

```
sudo wine launch.exe -WINEDLLOVERRIDES n,b
```

Is that correct?  BTW, after I typed in the correct login information I and clicked the "Start!" button I heard a sound effect and then a window with a titlebar that said "Message" popped up with some garbled text inside and a button that said "OK"

---

### Post by david_kt on 2007-04-09
No, it is not. I think it is better to run winecfg first:

```
winecfg
```

And then add new program, navigate to launch.exe in the BMO folder and press enter. After that, make sure you selected the launch.exe in your winecfg windows, and press library tab. And add mfc42 and syswin.

And don't run "sudo wine ...." just run "wine .....". Anyway, you could run it using the launcher.

DK

---

### Post by moot on 2007-04-10
> **david_kt said:**
> No, it is not. I think it is better to run winecfg first:

```
winecfg
```

And then add new program, navigate to launch.exe in the BMO folder and press enter. After that, make sure you selected the launch.exe in your winecfg windows, and press library tab. And add mfc42 and syswin.

And don't run "sudo wine ...." just run "wine .....". Anyway, you could run it using the launcher.

DK

When I try to add mfc42 and syswin to the library they don't show up in the list.  I noticed that they are also the only *.dll files in the system32 folder, all of the other *.exe files are just shortcuts to *.exe.so files in the /usr/lib/wine folder.

---

### Post by david_kt on 2007-04-10
> **moot said:**
> When I try to add mfc42 and syswin to the library they don't show up in the list.  I noticed that they are also the only *.dll files in the system32 folder, all of the other *.exe files are just shortcuts to *.exe.so files in the /usr/lib/wine folder.

How did you install wine? I think you have problems because you run "sudo wine" so that the wine files go to your system files instead of /user/.wine/......

May be you should try to remove wine completely, manually delete /usr/lib/wine folder, and delete /user/.wine folder, and then start new installation of wine and then your program in wine, as I mentioned before. But please remember do not run "sudo wine".

DK

---

### Post by moot on 2007-04-11
> **david_kt said:**
> How did you install wine? I think you have problems because you run "sudo wine" so that the wine files go to your system files instead of /user/.wine/......

May be you should try to remove wine completely, manually delete /usr/lib/wine folder, and delete /user/.wine folder, and then start new installation of wine and then your program in wine, as I mentioned before. But please remember do not run "sudo wine".

DK

I did all that and I still can't get it to work, it's kind of strange that such a simple game can't run correctly on Wine.

---

### Post by david_kt on 2007-04-11
> **moot said:**
> I did all that and I still can't get it to work, it's kind of strange that such a simple game can't run correctly on Wine.

Yes, it is strange. But I could easily launch this program although I did not sign in. Could you post here what the problem is after you reinstall wine?

DK

---

### Post by moot on 2007-04-11
> **david_kt said:**
> Yes, it is strange. But I could easily launch this program although I did not sign in. Could you post here what the problem is after you reinstall wine?

DK

OK, after deleting those two folders, completely un-installing Wine through SPM, re-installing it through SPM, adding those two *.dlls to the system32 folder, going through winecfg and finally running the launch.exe file in the terminal using wine rather than sudo wine here's exactly what happened:

The first window popped up like normal and I typed in my login information correctly and clicked the "Start!" button, which caused another window to open up and the wine terminal told me nothing:

[IMG]http://i48.photobucket.com/albums/f203/goldencream/Random/bm.png[/IMG]

I think that playing around with the setting in winecfg might fix this problem.

Just to make sure that this problem is on my end, please register for an Online Bomberman account (No email verification required, only username, password and nickname and the game is worth playing) at this address:

[http://www.broomop.com/Bomberman/register.php](http://www.broomop.com/Bomberman/register.php)

Then run the launch.exe file, input your username and password, set UDP to auto, click the Start! button and come back and tell us the results.

---

### Post by david_kt on 2007-04-11
I have tried and it is exactly as you said, no error message but it disappear. According to the site, it is related to internet connection problem. May be through wine the connection was failed. When I tried "dressing room" is said wrong password or wrong username.

DK

---

### Post by moot on 2007-04-11
> **david_kt said:**
> I have tried and it is exactly as you said, no error message but it disappear. According to the site, it is related to internet connection problem. May be through wine the connection was failed. When I tried "dressing room" is said wrong password or wrong username.

DK

Try forwarding the following UDP ports, then run the game again:

[http://z3.invisionfree.com/Bomberman_Online/index.php?showtopic=268](http://z3.invisionfree.com/Bomberman_Online/index.php?showtopic=268)

---

### Post by david_kt on 2007-04-13
I tried it on windows xp, it could load a screen and music, but that's it, it just disappeared. I think we should forget about online bomberman. Try offline bomberman instead hehehe.... :

[http://www.shdon.com/files/bomber.zip](http://www.shdon.com/files/bomber.zip)

DK

---

### Post by Broomop on 2008-05-13
thats because you need a username and password thats why it dissapeared...

---


---
title: "Ubuntu 12.10 won't run application\x-executable"
date: 2013-07-11
forum: Gaming &amp; Leisure
---

### Post by 00101010 on 2013-07-11
I recently installed Ubuntu to my desktop and tried to start a variety of games. None of them start. The two major problems being source games in steam and an MIT game called a slower speed of light. I experience the same problem with both execs and that is it doesn't seem like ubuntu even acknowledges that I'm trying to start the file. I'm new to the OS so I don't know how to start x-executables from the terminal to look for error but I've looked around the internet and it consistently seems to be a problem with openGL. Any help would be appreciated 'cause I just wanna get this fixed.


Addendum: These are all games that have been made to work with linux. I'm not trying to launch .exe files just linux executables

Addendum: I'm running Ubuntu 13.04 now but the problem still persists

Addendum: I rolled back my installation to 12.04 and the problem has been resolved

---

### Post by BreezyBrooke on 2013-07-11
You cant run Windows programs on Linux/Ubuntu. So every EXE you have, is useless on Ubuntu.

Edit:
Some good reading to a linux newb. :)
[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

---

### Post by 00101010 on 2013-07-11
I'm not running .exe I have Wine for that. I can't run legitimate linux execs. Files marked with extensions like .x86 or just not marked at all. In the properties they're described as being application/x-executable files.

---

### Post by CatKiller on 2013-07-12
To start an executable from the command line, you just type its name, as /path/to/file/file_name or, if you've already navigated to the appropriate place, ./file_name since the . means "this directory."

Linux-native Steam games come with launchers, you don't need to run them manually.

---

### Post by oldrocker99 on 2013-07-12
> **00101010 said:**
> I'm not running .exe I have Wine for that. I can't run legitimate linux execs. Files marked with extensions like .x86 or just not marked at all. In the properties they're described as being application/x-executable files.

Try this:

chmod +x name-of-program

Or this:

Open Properties for that file, click the Permissions tab and make sure that the Allow executable box is checked. 

Either way makes a program executable as far as the system is concerned, which **may** be your problem.

---

### Post by 00101010 on 2013-07-12
Using both  **oldrocker **and **CatKiller**'s methods yield the same results as if I where trying to launch the file from the GUI. The Terminal moves on to the next line and nothing opens, nothing is tracked by the terminal as it would if I opened Steam or Chrome.

---

### Post by LordFran on 2013-07-12
Same thing happens to me

---

### Post by efflandt on 2013-07-14
Do the Steam games work if launched from the "Library" in Steam? I believe Steam has to be running in order for the games to run (for Steam login and to save game state to the Steam Cloud). For example the Dash launcher for Team Fortress 2 runs
```
steam steam://rungameid/440
```

---

### Post by 00101010 on 2013-07-16
Steam games do not work from the launcher, I had heard of people who had the same problem with just steam games and troubleshot(?) them by launching their hl2 execs from the games source from the script and watching what errors pop up. But I can't launch any game whatsoever little lone a launcher reliant game without the launcher.

(?) The past tense of troubleshoot?

---

### Post by CatKiller on 2013-07-17
> **00101010 said:**
> Steam games do not work from the launcher

In general, this is false. If you're having problems with particular games, you'll have to get more specific.

You can drag-and-drop a launcher onto your text editor to see which command it runs, to enable you to run that command from the terminal. Steam puts its log somewhere funny and I can't remember where off the top of my head. If you launch Steam and run ps ax it'll be the line that starts with tee that will give you the location.

---

### Post by 00101010 on 2013-07-17
I wasn't trying to say that steam games to work from the launcher in all cases. I was saying that my steam games aren't working from the launcher. I tried the text editor trick with slower speed of light and the result was gedit froze, so I'm going to have to look into the game itself and see what common problems there might be. Using text editor on team fortress 2 gave me the steam rungame id and using that in the terminal gave me a very short command line stating the STEAM_RUNTIME ENABLED. I did run steam from the terminal though and the codes from steam are much longer and probably more useful in this case. It's mostly a lot of (steam:6436): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent. Trying to run Don't Starve gets the same effect of tf2. On the upside though minecraft runs just fine. The only reason for that I think is because it runs from a .jar and not from a application/x-executable file.

addendum: What I'm trying to say is that my games won't launch from the library they just don't open. Not that I launch my steam games without the steam launcher.

---

### Post by oldos2er on 2013-07-17
I downloaded 'A Slower Speed of Light', extracted it, changed directory to "A Slower Speed of Light" and ran ```
./A\ Slower\ Speed\ of\ Light.x86_64
``` It ran fine. If you're using 32-bit you'd run ```
./A\ Slower\ Speed\ of\ Light.x86
```

---

### Post by CatKiller on 2013-07-17
The location that I couldn't remember earlier and couldn't check is /tmp/dumps/*username*_stdout.txt. That's where Steam puts a lot of its output.

You can run some games directly from their executable without invoking Steam, but not all. It depends on the DRM that's been applied.

> **00101010 said:**
> It's  mostly a lot of (steam:6436): LIBDBUSMENU-GLIB-WARNING **: Trying to  remove a child that doesn't believe we're it's parent.

Yeah, I get that too. Pages and pages of it. Even when everything's running properly. There might be something else after that, though.

---

### Post by 00101010 on 2013-07-18
Thankz for all the help, I definitely learned a few tricks that will help me in the future. I'm not entirely sure what caused the problem but I'm going to go with a bad installation disk as this problem surfaced straight after installation. Now that I've rolled back my edition everything works as it should

---


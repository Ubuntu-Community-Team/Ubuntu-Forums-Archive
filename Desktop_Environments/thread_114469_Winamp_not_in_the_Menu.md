---
title: "Winamp not in the Menu"
date: 2006-01-08
forum: Desktop Environments
---

### Post by shade11 on 2006-01-08
I have recently Installed Winamp 0.a1-1 for Linux. I downloaded an RPM file and converted it to a DEB file. When I installed it i didnt see the Applications menu. So I re-installed it so I can show what I typed in the terminal

```
ian@Jevelxelwen:~$ sudo dpkg -i /home/ian/Desktop/winamp_0.a1-2_i386.deb
(Reading database ... 74500 files and directories currently installed.)
Preparing to replace winamp 0.a1-2 (using .../Desktop/winamp_0.a1-2_i386.deb) ...
Unpacking replacement winamp ...
Setting up winamp (0.a1-2) ...
ian@Jevelxelwen:~$


```

Do I have to tpye something up in the terminal or is there something I need to do? (And please dont tell me to install XMMS or BMP instead I already used them and I dont always like them.)

---

### Post by Lord Illidan on 2006-01-08
I think if you type winamp in the terminal, it should work.. though at the early stage it seems to be, you will probably run screaming back to XMMS....
Why not try Amarok?

---

### Post by lamego on 2006-01-08
I don't use winamp but I guess it should be available as "winamp" from a terminal window.
If you don't have a menu entire is because the package does not include one, just add a custom menu entry to launch it...

---

### Post by shade11 on 2006-01-08
I have typed it in the terminal, but no luck. I searched my File System for Winamp. But it just came up with the deb file I used.

I really want to use winamp. Unless someone can show me an mp3 decoder for Beep Media Player or an m4a/mp4/aac decoder for XMMS. OR if there is a media player that has that support. (Including wav and ogg support)

---

### Post by CarlosinFL on 2006-01-08
I did not even know Winamp was available for Linux...:confused:

---

### Post by shade11 on 2006-01-08
You can download it [here]("http://fileforum.betanews.com/detail/Winamp_3_for_Linux/1002748075/1")

Please Someone Help Me!!!

---

### Post by mcduck on 2006-01-09
[QUOTE=shade11]
I really want to use winamp. Unless someone can show me an mp3 decoder for Beep Media Player or an m4a/mp4/aac decoder for XMMS. OR if there is a media player that has that support. (Including wav and ogg support)[/QUOTE]
I don't know about winamp on linux, I find it hard to believe that it could be any better than XMMS/BMP. But have you already installed all codecs? After that you should have mp3's working in_every_ player :)

Try this: [http://www.ubuntuguide.org/#codecs]("http://www.ubuntuguide.org/#codecs")

You may also want to install mpg123, as that will enable preview of mp3 files in nautilus.

I'm not sure about m4a/mp4/aac, as I don't have any of those ;)

---

### Post by pmj on 2006-01-09
The command to start the program is "Winamp". The only thing I get when I run that, however, is an error message that goes "/usr/local/bin/Winamp: line 7: 11740 Aborted                 ${WADIR}/Winamp.exe $* >/dev/null 2>&1".

Anyway, I have agree with the others. There are many good music players for Linux, many of them better than Winamp.

---

### Post by shade11 on 2006-01-09
The thing is, is that I have XMMS and BMP. But I have to use both in order to play all my music. winap had that.

I either need XMMS to ru m4a/mp4/aac files. Or BMP to run mp3 files. and I already asked about XMMS m4a\mp4\aac file support, because it didnt seem to work.

---

### Post by steveneddy on 2006-01-09
If you are running Breezy5.10, then download [Automatix]("http://www.ubuntuforums.org/showthread.php?t=66563&highlight=automatix") and install everything it offers. You shouldn't have any problems after that. 

BTW, WinAmp sucks on Linux, use BMP or Xmms. Trust me, I've been down that road.

Also, please read the ENTIRE post before installing Automatix, OK? 

-StevenEddy

---

### Post by shade11 on 2006-01-09
[QUOTE=steveneddy]If you are running Breezy5.10, then download [Automatix]("http://www.ubuntuforums.org/showthread.php?t=66563&highlight=automatix") and install everything it offers. You shouldn't have any problems after that. 

BTW, WinAmp sucks on Linux, use BMP or Xmms. Trust me, I've been down that road.

Also, please read the ENTIRE post before installing Automatix, OK? 

-StevenEddy[/QUOTE]

I have already Installed Automatix. And the non-free decoders dont work with XMMS.

---

### Post by steveneddy on 2006-01-16
Your life sucks then.

---

### Post by newuser111 on 2006-01-16
I don't think alien converted rpms always work that well

this is an alpha release, so its probably very buggy but its too bad winamp didnt release deb since its not open source...

---

### Post by newuser111 on 2006-01-16
if you want m4a support in XMMS did you try sudo apt-get install xmms-mp4

it shows up in synaptic for me in the multiverse repos

---

### Post by shade11 on 2006-01-16
I have downloaded it and it seems to work.

---


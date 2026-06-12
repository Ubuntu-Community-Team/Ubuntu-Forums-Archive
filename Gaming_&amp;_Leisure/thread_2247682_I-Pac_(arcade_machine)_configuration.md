---
title: "I-Pac (arcade machine) configuration"
date: 2014-10-09
forum: Gaming &amp; Leisure
---

### Post by jorgerosa on 2014-10-09
Im creating an **"Arcade Machine" with Ubuntu**. Everything is already done, except...
I have an I-PAC (32 inputs) for the external player arcade buttons, it's connected to the PC by using an USB cable.

[IMG]http://sites.google.com/site/jorgerosaportfolio/home/ubuntu_i-pac2-hardware.jpg[/IMG]

The hardware from Ultimarc: [http://www.ultimarc.com/ipac1.html](http://www.ultimarc.com/ipac1.html)
The software: [http://www.ultimarc.com/download.html](http://www.ultimarc.com/download.html)
...And everything runs great in my MS Windows 7 (Just to be sure that the hardware is running ok).
Assign keys to it its easy, using their native Windows software.


BUT!... I want to use it in my **UBUNTU 14.04**, so...
1) I connect the hardware the same way (to an USB port in my PC)
2) I Downloaded and installed the lattest software: [IPACUTIL USB 0.7 (tar.gz)]("http://www.zumbrovalley.net/ipacutil/dnld/ipacutil_0_7.tar.gz")  *(command-line only)*
*Just a note: All these GNU/Linux software are from Travis: [http://www.zumbrovalley.net/readpost.php?artid=6](http://www.zumbrovalley.net/readpost.php?artid=6)*

After installed, i type in terminal:
[COLOR=#696969][I]sudo ipacutil --detect
[/I][/COLOR][COLOR=#000000]outputs:[/COLOR][COLOR=#696969][I]
Detect: found 1 I-PACs
I-PAC Board Number 0: unknown
Detection complete[/I][/COLOR]

Ok, my hardware seems to be detected... but... what I have to do now, to configure it?.... To assign a key to it?...
I've tried to install and run its GUI: [I-PAC GUI 0.3 (tar.gz)]("http://www.zumbrovalley.net/ipacutil/dnld/ipacgui_0_3.tar.gz")

If i do:  [COLOR=#696969]*gksudo ipacgui*[/COLOR]  then i enter the password, but nothing happens...

If i do:  *[COLOR=#696969]sudo ipacgui[/COLOR]*  outputs:  [COLOR=#696969]*command not found*[/COLOR]

If i do:  [COLOR=#696969]*ipacgui*[/COLOR]  outputs:  [COLOR=#696969]*Error: This program can only be run as root*[/COLOR]  (The GUI appears but that's all, as in next image)

[IMG]http://sites.google.com/site/jorgerosaportfolio/home/ubuntu_i-pac2-GUI.jpg[/IMG]

Note that even the i-PAC is not recognized there, in the "Devices column"...

Any help on this?...

---

### Post by jorgerosa on 2014-10-09
[SIZE=4]**SOLUTION:** [/SIZE]

I'll describe it here, step-by-step, the way how i've resolved my issue:
Note: I haven't used the "ipacgui"* (I've tried many ways but it just doesn't worked here)*

Install &#8220;ipacutil&#8221;. After being uncompressed...
[COLOR=#696969][I]make
sudo make install[/I][/COLOR]  

Running &#8220;ipacutil&#8221;:[COLOR=#696969][I]
sudo ipacutil
sudo ipacutil --detect[/I][/COLOR] (To detect the I-PAC)
[COLOR=#696969]*sudo ipacutil -w myipacconfig.cfg -t ipac2*[/COLOR] (To create an empty default config file)
I've opened the created &#8220;*myipacconfig.cfg*&#8221; and copy/pasted all the contents from &#8220;*ipac2_32.cfg*&#8221; to it, then...[COLOR=#696969][I]
sudo ipacutil --config myipacconfig.cfg 
[/I][/COLOR][COLOR=#000000][COLOR=#000000]Now, the terminal should output: [/COLOR][/COLOR][COLOR=#696969]*Programming I-PAC... ** I-PAC has been reprogrammed ***[/COLOR][COLOR=#000000][COLOR=#000000]

[/COLOR]**And... Everything runs great !!!** Configurations are not lost, even after i reboot the PC.
Of course using the GUI would be more user friendly but thats all i have now. No issues. Works 100%!
[/COLOR][COLOR=#008000]**Now i have an arcade machine powered by UBUNTU!... Isn't that nice !?...**[/COLOR][COLOR=#000000] [COLOR=#000000][IMG]http://ubuntuforums.org/images/smilies/icon_smile.gif[/IMG]
[COLOR=#008000]**YOUTUBE VIDEO:**[/COLOR] [http://www.youtube.com/watch?v=9DQ062gicPg&index=2&list=PLnhzSMPecj1Fe9Vx-O4YNGXoZMgLI_2UJ](http://www.youtube.com/watch?v=9DQ062gicPg&index=2&list=PLnhzSMPecj1Fe9Vx-O4YNGXoZMgLI_2UJ) *(The video shows the game itself and the I-PAC in use, too)* [/COLOR]
Hope this help someone else too![/COLOR]


**DESPERATE SOLUTION:**
There is yet other solution, to connect external buttons to the PC, without using I-PACs or any other hardware or software* (but I wanted to avoid this)*
Anyway here it goes, its explained in this video tutorial: [http://www.youtube.com/watch?v=MjfMXVpmxL8](http://www.youtube.com/watch?v=MjfMXVpmxL8)
[COLOR=#ff0000]**SOLVED...** But any other ways to use the GUI or tips, ideas or any other better solutions are all still welcome, ok guys?...[/COLOR][COLOR=#000000]

[/COLOR]

---

### Post by General_Faliure on 2014-10-10
Great, i have built mine 4 years ago, i use a minipac.
I have never got ipacutil / gui to work right, so i did the testing of the wiring with a windows xp machine :-(
I even did some mailing with Travis to troubleshoot the software, maybe i should give it another go.
All is working fine now by the way.
I use Lubuntu 14.04 now, because it's more lightweight (my first mainboard was based on an Athlon Xp 2100).
What frontend are you going to use? I use Mahcade, which is a fork of Wahcade.

Have a lot of fun.

---

### Post by jorgerosa on 2014-10-10
> **General_Faliure said:**
> "What frontend are you going to   use? My idea is not use a frontend, but have  only this game,  that i´m developing:
[https://www.youtube.com/watch?v=9DQ062gicPg&list=PLnhzSMPecj1HXo5IGrNFYiGyy6fHZYPTL&index=37](https://www.youtube.com/watch?v=9DQ062gicPg&list=PLnhzSMPecj1HXo5IGrNFYiGyy6fHZYPTL&index=37) I really want to **complicate** my life... lol

That frontend seems to be really cool. My idea (atm) is running UBUNTU OS and then it autostarts my game (Im developing the game, there will be no frontend, since only 1 game will be available to play).
 [SIZE=4]** · **[/SIZE]But later, after I get "tired" of this "pinball machine" project, I'll try frontends to be able to play many other games... That's for sure!.. ;)
[SIZE=4]** · **[/SIZE]Also I dunno about "Lubuntu", but since you say is a lightweight os, I think is just what I need now, so I'll digg on it and try it too. Thanks for the tips, General_Faliure! :)

---


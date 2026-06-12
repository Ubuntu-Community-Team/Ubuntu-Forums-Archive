---
title: "TuxBoy - Nintendo GameBoy emulator with GUI!"
date: 2007-08-03
forum: Gaming &amp; Leisure
---

### Post by Sockerdrickan on 2007-08-03
**[SIZE=3]No talk about where to get roms[/SIZE]**

TuxBoy 1.0 rc3 (september 8th) has been released! :KS

It's a fork of the open source GameBoy/Color emulator gnuboy.
It has several enhancements such as a GUI and Wiimote support, making it a very usable and fun emulator.
  
[IMG]http://img119.imageshack.us/img119/6066/tb0al3.png[/IMG]
Zelda in action.
Get it at [http://www.tuxemu.foo.se/](http://www.tuxemu.foo.se/) :guitar:

---

### Post by Nythain on 2007-08-03
now if you could get it to emulate gba and incorporate cheat code/memory hacking support i would love you

---

### Post by hikaricore on 2007-08-03
you sir, are brilliant

---

### Post by hikaricore on 2007-08-03
Wait I take part of that back.  You 7zipped it....  :lol:

---

### Post by Sockerdrickan on 2007-08-03
Got to love 7z compression ratios, eh? :lol: :lol:

---

### Post by hikaricore on 2007-08-03
Posted on UGA ^_^

Didn't have time last night.

---

### Post by DoktorSeven on 2007-08-03
Is it based on gnuboy source?  gnuboy was GPL, so we need sources if so. :)

---

### Post by Sockerdrickan on 2007-08-03
I know this is just beta :) release is october 1st

---

### Post by DoktorSeven on 2007-08-03
Still need source if you release any binary from GPLed source.  Personally I don't mind but I'm just warning you because some might really try to push you to do so...

---

### Post by Sockerdrickan on 2007-08-03
Ok! I'll release the source when the next beta arrives ( I'm warning anyone who's reading this it might be buggy and that's why I kept the horror to myself =) )

---

### Post by hikaricore on 2007-08-03
While I agree that the source needs to be released, I ask that **NO ONE** push the issue any further.
The last thing this thread needs is a flamewar.

If you absolutely must share your opinion on the matter of the source, then by all means do so through PM
or another method off of this forum.  You are all perfectly capable of holding back your egos for a few weeks
or whatever until the releaseof the next beta.

If at that time Tux0r does not release the source consider this post null and void then resume the flamewar.

Thanks,

--Aaron

---

### Post by DoktorSeven on 2007-08-03
> **hikaricore said:**
> While I agree that the source needs to be released, I ask that **NO ONE** push the issue any further.
The last thing this thread needs is a flamewar.


Absolutely, that's why I very gently reminded him of this.  It was just a simple warning that others might protest, just to make him aware of the fact.

Thanks for giving this warning.  I didn't want a flamewar either.

---

### Post by cogadh on 2007-08-03
> **hikaricore said:**
> While I agree that the source needs to be released, I ask that **NO ONE** push the issue any further.
The last thing this thread needs is a flamewar.

If you absolutely must share your opinion on the matter of the source, then by all means do so through PM
or another method off of this forum.  You are all perfectly capable of holding back your egos for a few weeks
or whatever until the releaseof the next beta.

If at that time Tux0r does not release the source consider this post null and void then resume the flamewar.

Thanks,

--Aaron
Damn you and your peace making ways, I'm in a really bad mood today and could have used a good flame war!:twisted:
*stomps out and heads for the Gamespot forums*

---

### Post by skoruppa on 2007-08-03
I really cant faind gui in this app... or im sa dump or tuxboy dont have gui :P
Ow, why without deb package and why with icon in menu when i must use terminal to run tuxboy oO"

TuxBoy file.gbc

oh and for now working better than Visual Boy Advance with game boy color games (form ubuntu repo) but vba HAVE gui :>

---

### Post by Sockerdrickan on 2007-08-03
H = SHOW GUI (1.0rc2 update: changed to P)

Why not deb etc: This is a beta remember! You know, I didn't even got it right with the licenses hehe! That will be fixed for beta2 though. :lol:

I have already done a few things, one of them is installation independence. (You don't have to install to run it)

---

### Post by Sockerdrickan on 2007-08-04
bump for source code hackers

source code august4 is online

---

### Post by stinger30au on 2007-08-04
looks ok

---

### Post by TheForkOfJustice on 2007-08-08
The menu entry does nothing!  You have to run Tuxboy from command line.  Even if I take the command I use in Terminal (to a specific rom) and use it as the command in the menu entry the game won't run!  The window will open but crash right away.

It needs a proper front end (or at least a stable one).

Also the sound runs a tiny bit slow.  This may also apply to the video but it's hard to tell with Gameboy.

Also, could you add a function that would speed up the game with one key/gamepad button press?  Pokemon battles can take forever some times.

---

### Post by Sockerdrickan on 2007-08-08
this is beta.
no speed up won't be implemented because it ruins the overall GameBoy experience, VBA has this if you must have it.


Exec works like this
(When installed) TuxBoy /home/robin/e/GB/zelda_ladx.gbc
(Running from dir with the rom in it) ./TuxBoy zelda_ladx.gbc

---

### Post by cogadh on 2007-08-08
I think what he's trying to say is he expected a GUI that launches with the emulator, allows you to browse for and select a rom, then run the rom. He didn't expect to have to run the GUI and rom from a single command in the terminal.

---

### Post by Sockerdrickan on 2007-08-08
Hey I know what he is saying alright, this is still beta and I have that yet to do!
I'm probably not going to write anything way advanced for the release candidate or 1.0
Probably a field where you can type the adress of the rom and below that maybe the dir you commonly use (It saves automatically after opening the rom) So it would go like


mario.gbc
/home/user/roms/gameboy

And as you guys might have already noticed this emulator is focused on GameBoy experience! :D Notice the WASD directional keys in the LEFT hand compared to classical emulators!

---

### Post by TheForkOfJustice on 2007-08-08
> **cogadh said:**
> I think what he's trying to say is he expected a GUI that launches with the emulator, allows you to browse for and select a rom, then run the rom. He didn't expect to have to run the GUI and rom from a single command in the terminal.

Oh, I expected it to be runnable from terminal.

The problem is that installing the package also produces an entry in the menu that does absolutely JACK SH!T! 

In order to run properly the program must be pointing to a ROM when it is run.  Like so:
```

TuxBoy /home/mackinal/ROMS-GB/PokemonCrystal.gbc
```

However, the menu entry is neither 'run in terminal' nor is it pointing at a ROM.  So as things stand now the program can not be run from the menu so either axe the menu icon or make a proper frontend!

As for the 'Gameboy Experience': just let the user decide how they want to play.  It's a really simple feature to be able to speed the clock up with a button press (and VBA sucks at the moment).

---

### Post by Sockerdrickan on 2007-08-08
No I already stated that this emulator is focusing on GameBoy experience and it of course shall be so!

"The problem is that installing the package also produces an entry in the menu that does absolutely JACK SH!T!"

I don't see how this icon is bothering you and it's just to get ready for the version that will use it.

---

### Post by chriswyatt on 2007-08-15
Looks promising so far ...

Sound is crackly on my setup and game doesn't run at correct speed, looking forward to future releases as I HATE the GUI for VirtualBoy under Linux, absolutely horrible.

---

### Post by Sockerdrickan on 2007-08-15
What's your CPU?

---

### Post by TheForkOfJustice on 2007-08-15
My processor is a Pentium III (Coppermine) and I have 256MB of RAM.

---

### Post by chriswyatt on 2007-08-16
Mine is a Centrino Duo 1.66 GHz with 2 Gigabytes of RAM.  Sorry, sound wasn't crackly (it just sounded that way on the game I tested it on) but it's choppy and the game doesn't run at a constant speed.  It's annoying because my processor should be more than capable of emulating a Gameboy, I do have sound problems with a lot of games so it could be something to do with my sound setup.

My sound card: Intel 82801G (ICH7 Family) High Definition.

EDIT: This is a problem in GNUBoy as well so I probably should post this in a seperate thread, sorry.

BTW, a skinnable GUI would be great in the future (I know that's probably a long way off), I remember an emulator for Windows a while back where the GUI was an actual Gameboy, I think it was VirtualBoy.

---

### Post by chriswyatt on 2007-08-16
> **Tux0r said:**
> Hey I know what he is saying alright, this is still beta and I have that yet to do!
I'm probably not going to write anything way advanced for the release candidate or 1.0
Probably a field where you can type the adress of the rom and below that maybe the dir you commonly use (It saves automatically after opening the rom) So it would go like


mario.gbc
/home/user/roms/gameboy

And as you guys might have already noticed this emulator is focused on GameBoy experience! :D Notice the WASD directional keys in the LEFT hand compared to classical emulators!

For a lot of Linux applications there is a generic dialogue box for opening files e.g. in OpenOffice, how easy would it be to have that in TuxBoy?

---

### Post by Sockerdrickan on 2007-08-16
That would kill ultra cross platform

---

### Post by Sockerdrickan on 2007-08-26
I find this new controls window more convenient
[img]http://img399.imageshack.us/img399/8869/guitg7.png[/img]

---

### Post by Jiiprah on 2007-08-26
Different Compression.

Could you host it as a .tar.gz or .rar or .zip? I can't open the 7zip.

---

### Post by Sockerdrickan on 2007-08-27
From the next release I will use 7z on pre compiled packages and tar.* on source
7zip can be obtained from add/remove

---

### Post by Sockerdrickan on 2007-09-14
TuxBoy 1.0rc released

Have fun! :guitar:

---

### Post by mocha on 2007-09-16
After installation I get:

```
bash: /usr/local/bin/TuxBoy: cannot execute binary file
```

the binary is there, I don't get it...

---

### Post by Sockerdrickan on 2007-09-16
Hmm :S Try to set permissions

---

### Post by mocha on 2007-09-16
Tried permissions and made sure it is set to executible, it still won't execute.

---

### Post by Sockerdrickan on 2007-09-16
That's weird. Anyone else has this problem?

---

### Post by TheForkOfJustice on 2007-09-16
Could it be because the only version of Tuxboy listed is the x86_64 version and not the x86 version?

I don't see the x86 download listed on the page.

---

### Post by Sockerdrickan on 2007-09-16
Nope you download the source and build it (2 seconds) if you want x86 32bit

---

### Post by mocha on 2007-09-19
> **TheForkOfJustice said:**
> Could it be because the only version of Tuxboy listed is the x86_64 version and not the x86 version?

I don't see the x86 download listed on the page.

I'm such a tard..  Yes, I was trying to run the 64 bit binary.  The 32 bit version runs fine after compile.  Sorry.

---

### Post by Sockerdrickan on 2007-09-19
Ok that's great to hear :D

---

### Post by Sockerdrickan on 2007-09-29
New site!! And forum.

[www.tuxemu.se.nu](www.tuxemu.se.nu)

---

### Post by Will B-R on 2007-10-28
How do you go about compiling the 32bit version?

---

### Post by Sockerdrickan on 2007-10-29
> **Will B-R said:**
> How do you go about compiling the 32bit version?

For 1.0 there will be source and a 32bit compiled version.
For now you can download the source and just type make in the directory :)

---

### Post by Origin on 2007-11-23
Strange... I've installed all the required libs using Synaptics Package Manager and then Tuxboy from the download, yet clicking on the icon under Games does nothing. I'm on Gutsy, x64. Would that be a problem?

---

### Post by Sockerdrickan on 2007-11-24
Yes that doesn't work for the moment...
You have to do ./TuxBoy romname.gb

---

### Post by Sockerdrickan on 2008-01-31
TuxBoy 1.0rc2 released
See post #1 for more information!

---

### Post by Sockerdrickan on 2008-02-26
Now with Wiimote support!

Wiimote, people!!!!!!!!

[http://www.youtube.com/watch?v=tCkFrF1PYJg](http://www.youtube.com/watch?v=tCkFrF1PYJg)

---

### Post by whoscheesemine on 2008-03-01
What would you guys recommend for playing GBA roms? VBA for linux makes my head tick to the left a lil bit. On my laptop (Dell Lattitude D520 Duel Booting Ubuntu and Tiny XP: Beast Edition) the Visual Boy Advanced works amazing on Ubuntu via WINE. The only problem I'm having now is using it with my younger brother's crappy MPC ClientPro 345 running Xubuntu. For what ever reason I can't figure out how to get WINE to open ANYTHING while in Xubuntu. On Ubuntu all I had to do was right click the .exe and then choose WINE from the application list on which program I would like to open the file with. However, on Xubuntu WINE doesn't show up on the application list. Try as I might using ''app finder''' and the search function there is no executible for WINE that I can find. All I can find is the executable for the configuration utility. Now, some how the last time I installed Xubuntu on his computer I managed to get it to work through WINE some how. Now that I think about it I think it might be that I added it to the application list and then when I restarted the computer it magically would open when I double clicked the .exe file. Hmmm... I'm gonna try that and I'll edit my post with how it worked. Oh, I thought I should also mention that when I did get it to work in the past, I couldn't access anything on the task pane of the Visual Boy Advance as it was behind Xubuntu's task pane. It was always kind of behind the task pane on my laptop, but I could still kind of click near it and have the drop down menu extend. I'll get back to you guys on this.

---

### Post by mocha on 2008-03-02
Mednafen seems to be the only good option for GBA.  No GUI, but at least it works and looks good once you setup the CFG file properly.

---

### Post by frenchn00b on 2008-03-02
```
 apt-cache search gameboy
gngb - GameBoy Emulator
mednafen - multi-platform emulator, including NES, GB/A, Lynx, PC Engine
z80asm - assembler for the Zilog Z80 microprocessor
xmess-sdl - SDL binaries for the Multi Emulator Super System
xmess-x - X binaries for the Multi Emulator Super System
```

is tuxboy superior to those previous ones ?

---

### Post by Sockerdrickan on 2008-03-02
It's a fork of

```
sudo apt-get install gnuboy-sdl
```

and is superior to it yes. Probably better than the other ones when it comes to GB/C emulation.

---

### Post by fktt on 2008-03-27
Hopefully, around when might the GUI become usable(for loading roms i mean)? :)

---

### Post by Sockerdrickan on 2008-03-28
Yeah it's still in development 1.0 will be released this year. :)

I believe the Wimote support will be quite popular.

---

### Post by hessiess on 2008-03-28
> **Tux0r said:**
> Yeah it's still in development 1.0 will be released this year. :)

I believe the Wimote support will be quite popular.

I don't see what advantage motion sensing(analogue input) or the other features of the wiimote would be for an application that is emulating a device which only supports digital input:confused:

---

### Post by Sockerdrickan on 2008-03-28
Just the fact that you will be able to play from your bathroom is thrilling enough.

---

### Post by grossaffe on 2008-03-28
> **Tux0r said:**
> Just the fact that you will be able to play from your bathroom is thrilling enough.

you can already do that with a real gameboy...

---

### Post by Sockerdrickan on 2008-03-28
> **grossaffe said:**
> you can already do that with a real gameboy...

That's the point.

---

### Post by chriswyatt on 2008-04-02
Thanks for this, I've been wanting a Gameboy emulator with a decent GUI for Linux, not keen on the one for VisualBoy (hate it actually).  Looking forward to the final polished version :) .

---

### Post by Sockerdrickan on 2008-04-02
Yes the new GUI is much better just so you know.
[img]http://img27.picoodle.com/img/img27/4/3/30/f_newguim_4cf277d.png[/img]

---

### Post by grossaffe on 2008-04-02
so does the gui work for opening ROMs yet?

---

### Post by Sockerdrickan on 2008-04-03
Yes I believe it does with the current version too, it's just that the code for actually cleaning up the memory and loading a new rom isn't.

---

### Post by grossaffe on 2008-04-03
> **Tux0r said:**
> Yes I believe it does with the current version too, it's just that the code for actually cleaning up the memory and loading a new rom isn't.

oh, so you can load one rom, but you can't stop and then load another one?  good enough for me.

I won't have any problem running this on 64-bit, will I?

---

### Post by Sockerdrickan on 2008-04-03
You can compile it as a 64 bit binary with no problems at all.

---

### Post by grossaffe on 2008-04-03
hey, you've got a new web-page!

edit: ok, linux noob :(.  how do i compile and install?
reedit: nevermind, just dependency issues.

---

### Post by TheForkOfJustice on 2008-04-23
Having trouble with TuxBoy1.0RC2

Can't make it run.  I type 

./TuxBoy.i686 roms/rom.gbc

just like you mention in the INFO file but I get an error instead:

bash: ./TuxBoy.i686: Permission denied

I have all of the permissions and all of the dependencies.  What am I missing?

---

### Post by Sockerdrickan on 2008-04-24
I would guess you would have to find the binary with your terminal and do a
```
chmod +x TuxBoy.i686
```

---

### Post by TheForkOfJustice on 2008-04-24
> **Tux0r said:**
> I would guess you would have to find the binary with your terminal and do a
```
chmod +x TuxBoy.i686
```

Bingo! Works.

I take it that I can't run it like this:

```
~/tuxboy/TuxBoy.i686 roms/rom.gbc
```

because I get a 'Signal 11' error (whatever that means)

I have to use a Terminal that is already in TuxBoy's home folder, don't I?

---

### Post by Sockerdrickan on 2008-04-25
Yeah but the next release will have a working open rom dialog, isn't that about time? :P

---

### Post by disturbedite on 2008-04-25
> **Tux0r said:**
> Yeah but the next release will have a working open rom dialog, isn't that about time? :P
is there an ETA on this new version?

---

### Post by Sockerdrickan on 2008-04-25
August 1st is the absolute latest date, maybe earlier.

---

### Post by KaroSHiv0n on 2008-05-07
Whenever i try to download the file from your site i get redirected to [http://kwikphp.com/blog3/](http://kwikphp.com/blog3/) 

where can i download the source? :D:lolflag:

---

### Post by Sockerdrickan on 2008-05-07
keep on trying
****ing host

---

### Post by giacomok on 2008-05-28
> **KaroSHiv0n said:**
> Whenever i try to download the file from your site i get redirected to [http://kwikphp.com/blog3/](http://kwikphp.com/blog3/) 

where can i download the source? :D:lolflag:

what I have to do to download tuxboy? 
I don't understand the answer      
[I]keep on trying
****ing host[/I]
could you share the source in this thread whit an Attachment?
thanks a lot
and excuse-me for my bad english...

---

### Post by Sockerdrickan on 2008-05-28
I really don't see any problem, it works [www.tuxemu.se.nu](www.tuxemu.se.nu)

---

### Post by giacomok on 2008-05-28
when I try to download tuxboy from the link [TuxBoy 1.0rc2 (Linux)]("http://tuxemu.byethost31.com/zip/tuxboy_1.0rc2.zip") appear this message:
YOU ARE VIEWING THE OLD WEBSITE
PLEASE WAIT WHILE YOU ARE REDIRECTED 
and I am redirected to this blog: [http://kwikphp.com/blog3/](http://kwikphp.com/blog3/)
and then to this [http://ifastnet.com/hosting-blog/index.php](http://ifastnet.com/hosting-blog/index.php)

---

### Post by TheForkOfJustice on 2008-05-28
It's the 'Quicklinks' section that's buggy and sends you to the ad-infested site.

If you select 'Downloads' from the upper menu instead you can get the file.

---

### Post by Sockerdrickan on 2008-05-28
Well if you were to be a good boy and downloaded it from the download page you would not have been redirected to garbage.

---

### Post by giacomok on 2008-05-28
then I'm not a good boy... 

thanks everybody

---

### Post by Sockerdrickan on 2008-05-28
have a good one

---

### Post by Nachtholm on 2008-05-29
I have two questions:

1) does TuxBoy play compressed roms?
2) Is there any chance for GBA support in the future?

---

### Post by Sockerdrickan on 2008-05-29
1) no
2) way no

---

### Post by Sockerdrickan on 2008-05-30
Guys, I'm currently thinking about pushing out 1.0 rc3 on June 1st instead of August 1st...

The changes would be

new gui
wiimote support
more code cleanup
compiles on windows

**but** it would still lack a working open rom dialog.

Anyone able to give me a boot kick in the *** to get it out, or should I wait 2 more months?

---

### Post by Sockerdrickan on 2008-09-08
1.0 rc3 released!
Wiimote support :lolflag: :D :D

---

### Post by blacksky2 on 2008-10-04
hay could you give me a hand iv tried running it acompiling it but just keeps saying signal 11, (already tried: chmod -x, sudo, sudo su, su-c)

---


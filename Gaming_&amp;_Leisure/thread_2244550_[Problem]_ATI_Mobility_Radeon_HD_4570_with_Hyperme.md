---
title: "[Problem] ATI Mobility Radeon HD 4570 with Hypermemory Technlogy"
date: 2014-09-17
forum: Gaming &amp; Leisure
---

### Post by FranciscoFeijoo on 2014-09-17
Morning Guys!

I am kinda new on Linux world and i am really enjoying this! but i have a small question
during my work on "field" of Ubuntu, i found out that he recognize my graphic card as a Gallium 0.4 on AMD RV710 witch is kinda wrong because my laptop have a ATI Mobility Radeon HD 4570 with Hypermemory Technlogy.

I would like to know how do i update this and update my graphic card so  i can have the 100% preformance of it during games.

Can anyone help me?
;)
[COLOR=#6D6F72]




[/COLOR]

---

### Post by maxinstuff2 on 2014-09-17
[FONT=arial]AMD (and Nvidia for that matter) often repackage an re-release GPU's with slight changes. 

Things like adding memory, or clock speed, but otherwise leaving the architecture the same.[/FONT]

What I would suggest is make sure you have installed these packages:
```
[COLOR=#333333][FONT=UbuntuMono]sudo apt-get install xvba-va-driver libva-glx1 libva-egl1 vainfo[/FONT][/COLOR]
```[COLOR=#333333][FONT=UbuntuMono]

[/FONT][/COLOR][FONT=UbuntuMono][FONT=arial]Taken from the wiki - the whole page is a very good guide on dealing with the AMD drivers in general:[/FONT][/FONT][COLOR=#333333][FONT=UbuntuMono]
[/FONT][/COLOR]https://help.ubuntu.com/community/BinaryDriverHowto/AMD

---

### Post by FranciscoFeijoo on 2014-09-17
nop didn't had that! thanks.but  is that enuff? will i see some difrence during like playing a game? i mean will run more smoothly?

ps. that totaly messed up my ubuntu. how do i unistall it and put it the normal drives? after log in on ubuntu i cant do anything don't appear a thing

---

### Post by maxinstuff2 on 2014-09-17
Actually - that card is listed as "fully supported" by the Radeon (default) drivers. 

So I don't think you need to do anything. In fact I don't think you even needed the packages above. I erroneously assumed you were using the fglrx drivers (which you don't need). 
If you want to remove those packages:
```
sudo apt-get remove [COLOR=#333333][FONT=UbuntuMono]xvba-va-driver libva-glx1 libva-egl1 vainfo
```


[/FONT][/COLOR]

---

### Post by FranciscoFeijoo on 2014-09-17
i can't even get to the terminal. i log in and it frezes there.. i need to restore the old defenitions how?

---

### Post by maxinstuff2 on 2014-09-17
Press Alt+Ctrl+f1 to switch to a virtual console.
then you can log in to just command line and do it.

---

### Post by FranciscoFeijoo on 2014-09-17
i did that and no fix :| Boot -Repair with this?

---

### Post by maxinstuff2 on 2014-09-18
Go into recovery mode by pressing shift at boot.
from there you can choose root command line and do it there.

---

### Post by mastablasta on 2014-09-18
well, you got a totally wrong advice. but would be helpful to know now what is not working and what is (any error messages).


> **FranciscoFeijoo said:**
> 
during my work on "field" of Ubuntu, i found out that he recognize my graphic card as a Gallium 0.4 on AMD RV710 witch is kinda wrong because my laptop have a ATI Mobility Radeon HD 4570 with Hypermemory Technlogy.

[COLOR=#6d6f72][/COLOR]
that is not true that you card was not recognised by opensource driver (if it wasn't then you wouldn't see any desktop).

RV710 is the code of the chip that is included in these models:
RV710/RV730                 Radeon HD 4330/4350/4550/4650/4670/5145/5165/530v/545v/560v/565v

and as you can see here: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver) you had full 3D support.

> 
To see your OpenGL information, you can run the commands below. Make sure your OpenGL renderer string does not say "software rasterizer" or "llvmpipe" because that would mean you have no 3D hardware acceleration: ```
sudo apt-get install mesa-utilsLIBGL_DEBUG=verbose glxinfo
```


I am not sure how to solve this mess other than removing the installed libraries. but perhaps you can also find some information here: [https://help.ubuntu.com/community/BinaryDriverHowto/AMD](https://help.ubuntu.com/community/BinaryDriverHowto/AMD)

---

### Post by maxinstuff2 on 2014-09-18
It wasn't even advice, it was unneccessary rubbish and for that I am sorry :(
I should not have assumed you were using the proprietary drivers.

Please let us know if you were able to remove those packages. 
I am actually quite surprised it borked your display though...

---

### Post by FranciscoFeijoo on 2014-09-18
yeah no solution.. i think. basicly after log in it's totally frozed no menu at left mouse move but can't do anything..

Solution for this? :O

---

### Post by maxinstuff2 on 2014-09-18
Uninstall the packages from recovery mode.

Press shift at boot to get grub menu, select recovery mode.

Then you will get a screen where you can select from a list of options, one of the is "root" which will drop you into root command line.
Then do these lines one at a time, this will mount your hard drive in read/write mode, and uninstall the packages:
```
mount -o remount, rw /
apt-get remove [COLOR=#333333][FONT=UbuntuMono]xvba-va-driver libva-glx1 libva-egl1 vainfo[/FONT][/COLOR][COLOR=#333333]
```[/COLOR]
[COLOR=#333333][FONT=UbuntuMono]
[/FONT][/COLOR]

---

### Post by FranciscoFeijoo on 2014-09-18
yes sir! let's try that

---

### Post by FranciscoFeijoo on 2014-09-18
not didn't work.. any more solution? :| getting mad.. lol

---

### Post by QIII on 2014-09-18
Hello!

I'm on a train headed to work right now, so it would be difficult to help fully, but I will try to check in within a few hours.

This can be fixed, but it will involve reinstalling some packages to make sure everything is there and reconfiguring xorg. 

Hang tight.  There are several people I know of who are very knowledgeable in this subject who may step in in the meantime.

Be aware that the advice given was ill-advised -- but it was well-intentioned.  So don't be too mad.

Edit:  some information would be helpful:

Please get back to recovery mode and mount / rw as you did before.  Instead of uninstalling anything,  issue the following command, but DO NOT reply "y" at this time:

```
apt-get autoremove
```

You will not be able to take a screen shot, so please use a cell phone camera to get a picture of the results.  Post the image here using the "paper clip" icon above the text entry box.

Then answer "n" to the prompt.  I want to first see what else might have been installed and can be cleaned up before proceeding.

---

### Post by FranciscoFeijoo on 2014-09-18
i can post here a photo with mobile ofc from the case. the resolution changed when i rebooted laptop after put the 1st update. and after i put the password for log in he just dont freeze the mouse. and on top left of the monitor appears a small windows saying that there was a problem and with 2 bottons, 1st quit 2nd, report. i tryed click on the report but no effect what so ever of anything.

1 thing
everytime i put on root the command > [COLOR=#000000][FONT=Ubuntu Mono]mount -o remount, rw /[/FONT][/COLOR] theres no reaction what so ever. is it normal?

---

### Post by QIII on 2014-09-18
There is a typo in the command -- an extra space.  It may make no difference, but it should be

```
[COLOR=#000000][FONT=Ubuntu Mono]mount -o remount,rw /[/FONT][/COLOR]
```

All you should see is a new prompt appearing below the one you issued the command in.  Nothing special happens that you can see.

The command is simply telling the system to let you have read/write permission on / so you can make changes.  When you first enter the recovery mode, you have mounted the system read-only.  You need to remount it in read/write mode.

When you have done that, the "sudo" is unnecessary in the commands suggested above.  You are already effectively the root user.  So be careful what you do.

Whatever you do, don't try to install the proprietary fglrx driver.  It will not work with that adapter on any release of Ubuntu after 12.04.1.  AMD no longer supports cards prior to the HD 5000 series on Linux.

As for xvba-va-driver and all, notice that it is in a section of the wiki about installing the proprietary driver from the command line.  I put those instructions there for a reason:  Those packages work only with the proprietary driver's APIs.  I don't even know what to think about what might have happened installing them as you did.

maxinstuff2 was trying to help.  I just wish I'd have seen this earlier...

Like I said, this can likely be fixed.  If you could, please post an image of the information I asked you for.

---

### Post by FranciscoFeijoo on 2014-09-18
ok gonna try it right now. just getting home from office.

---

### Post by FranciscoFeijoo on 2014-09-18
i tryed but this was the result (ps. i am new to linux sorry if i made any wrong move or step or something :S)

---

### Post by QIII on 2014-09-18
That's good.  That means there are no extra packages that were dragged in, so nothing to clean up.

Next step: Did you at any time try to install the ATI driver "fglrx"?

EDIT:  Not accounting for a language barrier before, let me add this:  If you did not try to install it, DO NOT TRY NOW!

;)

---

### Post by FranciscoFeijoo on 2014-09-18
i didnt. i did what was sed on the 1st answer in this topic. and then restarted ubuntu by my selfe becoz was having probs on internet conection and realized this problem.

---

### Post by QIII on 2014-09-18
OK.  Good.

Now we need to reinstall some things that are installed by default to be sure they are in good order.

There are two possible versions of the next step.  

Try this one first.  Attach an image of the result.

Still from recovery mode:

```
apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
```

---

### Post by FranciscoFeijoo on 2014-09-18
ok so i put > [COLOR=#000000][FONT=Ubuntu Mono]mount --o remount, rw  /[/FONT][/COLOR] and then that code right?

---

### Post by QIII on 2014-09-18
If you haven't left the recovery mode, there is no need to remount.

And remember to remove the space I indicated if you do.

Then yes, enter the command and run it.

Edit:

I also see you have an extra dash in there now.

Remember, it's

```

[COLOR=#000000][FONT=Ubuntu Mono]mount -o remount,rw /
```[/FONT][/COLOR]

---

### Post by FranciscoFeijoo on 2014-09-18
i sed "Y" reloaded ubuntu keeps same.

i have dualboot thats why i takes kinda time for do this

now what?

---

### Post by Bashing-om on 2014-09-18
FranciscoFeijoo; Hello;

As QIII is taking a break, let me fill in for a bit.

Yeah, that looks good ! Reboot and let's see the effect.

We can expect you to come up on the open source driver to your normal login -> desktop .

[INDENT][INDENT]all good now ?
[/INDENT][/INDENT]

---

### Post by FranciscoFeijoo on 2014-09-18
nop keeps same problem.

---

### Post by QIII on 2014-09-18
OK.  Sorry.  Back now.  Had to do some actual work at work!  

Next step:

```
dpkg-reconfigure xserver-xorg
```

and reboot.

---

### Post by FranciscoFeijoo on 2014-09-18
> [COLOR=#000000][FONT=Ubuntu Mono]mount -o remount,rw /
[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]dpkg-reconfigure xserver-xorg[/FONT][/COLOR]

in this order?

---

### Post by QIII on 2014-09-18
You've already reinstalled the mesa stuff.

So just mount the file system and 

```
dpkg-reconfigure xserver-xorg
```

then reboot.

---

### Post by Bashing-om on 2014-09-18
FranciscoFeijoo; well,

While it will not hurt to run the 'apt-get' commands, it is not necessary - once is enough.
Just run the " dpkg-reconfigure xserver-xorg " . Are you still having to boot to "recovery mode" ? Then remounting to read/write will also be required.

While we await your regularly scheduled 1st responder -

[INDENT][INDENT]as I do pass by
[/INDENT][/INDENT]

---

### Post by FranciscoFeijoo on 2014-09-19
Sorry the late reply.. I fixed this with a simply solution. re-install Ubuntu. i guess was more easy and less work for you all and for me :D
in mean while back to the topic for what my cousin sed me and he is kinda good with Ubuntu, he sed that my drives for my graphic card only aviable in the lower version of ubuntu (last one i think) is it possible?

Ps. thanks for the help you all!

---

### Post by QIII on 2014-09-19
Well, not a solution to the immediate problem.  But an effective alternative.

The open source driver works just fine and includes 3D support.

The distinction is that the proprietary ATI driver does not work for that card because ATI dropped Linux support for it.

The last Ubuntu release for which a driver is available for that card is 12.04.1.  It won't work in 12.04.2 or later.  Installing the current 12.04 wont't work -- so don't just go download 12.04.

---

### Post by FranciscoFeijoo on 2014-09-19
so ther's no solution for it?

---

### Post by QIII on 2014-09-19
If by "solution" you mean "installing the ATI proprietary driver" so it will work with your adapter, then I am afraid not.

The legacy ATI driver that AMD/ATI has available for that adapter is no longer under development, so it has not been updated to work with the newer graphics stack used after 12.04.1.

Since proprietary drivers are written by OEMs (not OS developers) there is nothing the Linux community can do other than work on the open source driver.  The same is true for Windows.  MS does not write drivers for ATI GPUs.  AMD/ATI does.

The difference is that the graphics stack in Windows changes so little over time that the legacy driver still works.  If you were running Windows and intalled the ATI driver, you would still find that the driver is identified as "legacy" -- as it is on my Windows 7 machine with an HD 4000 series card.

If you want a proprietary driver from ATI that will work, you'll have to install 12.04 or 12.04.1.  12.04.2 or later simply will not work.

---

### Post by Bashing-om on 2014-09-19
FranciscoFeijoo; Morning;

We have given you our "solution", install release 12.04[color=red].1[/color]. If you must have a proprietary driver with that card; that is the only current release that the provider, AMD (ATI), supplies a driver for. 

Else it is a real ugly hack, and you are asking for big trouble. We DO NOT support a hack !

[INDENT][INDENT]make do with what is
[INDENT][INDENT][INDENT][INDENT]and be happy
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by FranciscoFeijoo on 2014-09-19
sorry if you tought i was asking for something like big trouble, believe me i'm not. i just don't understand alot our humm.. nothing about Linux and Ubuntu and thats why for me everything about terminal codes to specs of a graphic card is kinda chinese for me. sorry !

---

### Post by Bashing-om on 2014-09-19
FranciscoFeijoo; Hey ;

That is not a problem, We are all at some stage in this learning curve.
Here is the skinny on AMD:
> 
IF its an HD 2x/3x/4x then you are out of luck as AMD announced <last> summer that it is relegating these chipsets to legacy status and will not be developing new drivers for them. Existing restricted drivers from AMD won't work either, because they require X-server v1.12 and Ubuntu 12.10 uses X-server v1.13.
That's because, starting with Ubuntu 12.04.2, the X-server version was updated to a newer version that is now incompatible with the HD 2x/3x/4x series AMD cards. [Terminal command -> X -version to determine the x-server version.]
(Mark Phelps)


There are many ATI cards in this category still on the retailers shelf and it is sad that AMD has chosen not to support the cards after they purchased ATI .

[INDENT][INDENT]But, that is the way it is
[/INDENT][/INDENT]

---


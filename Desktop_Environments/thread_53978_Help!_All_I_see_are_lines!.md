---
title: "Help! All I see are lines!"
date: 2005-08-02
forum: Desktop Environments
---

### Post by sarimalia on 2005-08-02
evenin' all...

so perhaps I was a bit ambitious in getting my new system and wanting to dive into linux with no experience whatsoever. i figure it'll be an adventure at least...

anyway, i just tried to install kunbuntu, and it went through everything on the install disk, but when it came time to load, all i get are multi-colored stripes up and down my screen. i can't get beyond that point.

does anyone know what could be causing this and how i can remedy it? 

thanks in advance for your help!

sari

---

### Post by amohanty on 2005-08-02
> but when it came time to load, 

When was this? At first boot or at the end of the installation?

AM

---

### Post by ltmon on 2005-08-02
Ouch! That sounds bad!

A couple of questions:
- What's your system?  In particular, what video card and monitor do you have?
- Have you ever run a different Linux distro successfully?
- Have you run the live cd before?  If you do have the Ubuntu live cd, or any other live CD available try it out.

Those answers will help a bit.

Now... the following sequence may help, but then again it may not: 

Hold down CTRL-ALT-F1, and you should get a text prompt.  Assuming that worked you can login in text-only mode.

Type at the prompt:

> sudo /etc/init.d/kdm stop

Which will stop the graphical display completely (it's still running in the background before you do this).

Then type:

> cp /etc/X11/xorg.conf ~/xorg.conf.backup

This creates a backup of your display configuration, just incase things get worse instead of better.

Now:

> sudo dpkg-reconfigure xserver-xorg

This will start a series of guided questions to reconfigure your display (Xserver).  If you don't understand the question, take the default.  If you do understand the question, do a quick sanity check on the default and change it if need be (e.g. if it gets your video card completely wrong or something).

Once through with this, try starting the display again:

> sudo /etc/init.d/kdm start

And see if it works.

Good luck!

L.

---

### Post by sarimalia on 2005-08-03
[QUOTE=amohanty]When was this? At first boot or at the end of the installation?

AM[/QUOTE]


end of installation...

---

### Post by sarimalia on 2005-08-03
[QUOTE=ltmon]Ouch! That sounds bad!

A couple of questions:
- What's your system?  In particular, what video card and monitor do you have?
- Have you ever run a different Linux distro successfully?
- Have you run the live cd before?  If you do have the Ubuntu live cd, or any other live CD available try it out.

Those answers will help a bit.

Now... the following sequence may help, but then again it may not: 

Hold down CTRL-ALT-F1, and you should get a text prompt.  Assuming that worked you can login in text-only mode.

Type at the prompt:

> sudo /etc/init.d/kdm stop

Which will stop the graphical display completely (it's still running in the background before you do this).

Then type:

> cp /etc/X11/xorg.conf ~/xorg.conf.backup

This creates a backup of your display configuration, just incase things get worse instead of better.

Now:

> sudo dpkg-reconfigure xserver-xorg

This will start a series of guided questions to reconfigure your display (Xserver).  If you don't understand the question, take the default.  If you do understand the question, do a quick sanity check on the default and change it if need be (e.g. if it gets your video card completely wrong or something).

Once through with this, try starting the display again:

> sudo /etc/init.d/kdm start

And see if it works.

Good luck!

L.[/QUOTE]

------

it's a new laptop that i just got yesterday, built on an asus whitebook. video card is, well, crap. the website says intel integrated graphics. doesn't list the particular card.

never done the linux thing ever. i knew that ubuntu was supposed to be compatible with most systems...

i haven't done the live cd. i don't have one here. i think there may actually be one packed up somewhere right now, but i'm mid crazy move from hell.  ](*,) 

i'll try the prompts you said to. and will do default because i have no clue about anything else. ;-) if it doesn't work, how do i erase everything and attempt to reinstall, be it kubuntu or another distribution? i can't even figure out the command to do that.

thanks!
sari

---

### Post by sarimalia on 2005-08-03
ok tried steps above. ended up with lines still... 

i redownloaded the isntall stuff onto my friend's computer so i can burn another copy and see if perhaps the install disk had something wrong. but still can't find a way to delete the HD and start over. any commands that will do that?

if this doesn't work the second time, do you guys have a rec for a distribution that *may* work? i'd hate to have to resort to windows. i hate windows. sigh. and when recommending, i guess keep in mind that i'm better than the lay-computer user, but i'm no power programmer tech god. :-)

thanks all...
s

---

### Post by coolclassic on 2005-08-03
After putting in the install disk it will set up the HD for you.
Other distro to try Suse9.3

---

### Post by sarimalia on 2005-08-03
[QUOTE=coolclassic]After putting in the install disk it will set up the HD for you.
Other distro to try Suse9.3[/QUOTE]

i did the install last night. now it doesn't run off of the cd... if i DON'T need to erase everything to reinstall, how do I get the computer to read the disk instead of what is installed?

and will research suse now. thanks. :-)

---

### Post by coolclassic on 2005-08-03
I'm a bit confused if you are installing ubuntu on to a HD you will not need the cd for it to work unless you are using a live cd if this was the case you would not be installing to a HD.

If the computer is not reading the CD at boot it could be that your bios is not setup to allow booting from cd.

---

### Post by sarimalia on 2005-08-03
no. i used the install cd... but then you'd said something about running off of the cd, so i got confused.

so no, it doesn't need the cd right now. it also doesn't work at all!!! eek!

i think i should just delete and start everything over, clean slate. either with ubuntu or another dist. but i feel like such a stupidhead not able to even figure out a way to do so.

blegh.

thanks again guys.

---

### Post by amohanty on 2005-08-03
For a clean install heres what I do, other ways exist but I used to it:
1. downlaod win98se bootdisk from bootdisk.de
2. boot from floppy
3. >> fdisk /mbr
4. >> fdisk 
      remove all partitions
5. put in ubuntu live cd (this runs linux off of the cd - no install required).
    see if this boots into ubuntu and everything works or not. If it doesnt post the results. You could also try the knoppix live cd (google it)
6. If everything works, install from Ubuntu install cd 

AM

---

### Post by sarimalia on 2005-08-03
[QUOTE=amohanty]For a clean install heres what I do, other ways exist but I used to it:
1. downlaod win98se bootdisk from bootdisk.de
2. boot from floppy
3. >> fdisk /mbr
4. >> fdisk 
      remove all partitions
5. put in ubuntu live cd (this runs linux off of the cd - no install required).
    see if this boots into ubuntu and everything works or not. If it doesnt post the results. You could also try the knoppix live cd (google it)
6. If everything works, install from Ubuntu install cd 

AM[/QUOTE]

1. easy enough
2. don't have floppy, does usb key work instead?
3&4.   huh?!
5. gotta download it...
6. fingers crossed

---

### Post by Hikaru79 on 2005-08-03
Your issue seems to be a problem with your X-org settings. Chances are you didn't set the right graphics adapter. The right graphics adapter for your card is: i810 . Now, try this:

sudo vim /etc/X11/xorg.conf

And in that editor (use nano if you're not familiar with vim, its an acquired taste), find a line towards the end that says: 

Section "Device"

Under that heading, there should be a line that says "Driver" and then the name of a driver. If that name ISN'T "i810", change it to "i810". Then, save that file, restart, and tell us what happens.

If this doesn't work, I have other tricks up my sleeve, don't worry :) Don't give up and reinstall, chances are there is no need to do so.

---

### Post by amohanty on 2005-08-03
> 2. don't have floppy, does usb key work instead? 

Yup just set up removable media to be your first boot source in the BIOS.

> 3&4. huh?! 

fdisk is a utility to partition drives. 
fdisk /mbr cleans out the MBR


However I would suggest trying Hikaru's suggestions. Re-install is an extreme option and should be avoided as far as possible.

AM

---

### Post by sarimalia on 2005-08-03
[QUOTE=amohanty]Yup just set up removable media to be your first boot source in the BIOS.

 

fdisk is a utility to partition drives. 
fdisk /mbr cleans out the MBR


However I would suggest trying Hikaru's suggestions. Re-install is an extreme option and should be avoided as far as possible.

AM[/QUOTE]

it's definitely i810. no change there.

how do i do said action in the bios? 

why is it bad to erase and reinstall? call me curious...

---

### Post by amohanty on 2005-08-04
> how do i do said action in the bios? 

Well in the CMOS setup there should be menu item called boot. in there you should be able to setup the boot order what goes first second and so on. If you select removable media as the first (provided your bios has that option) you sould be good to go.

> why is it bad to erase and reinstall? call me curious... 

time consuming
loss of data
lack of information as to what went wrong which means you can repeat the problem.
e.g. I just completely borked my system while playing HL2 on cedega. Have no frigging idea but will probably spend a couple of days on it before even considering a reinstall. It may not be for everybody but it helps so that I dont do it again.

AM

---

### Post by sarimalia on 2005-08-04
[QUOTE=amohanty]Well in the CMOS setup there should be menu item called boot. in there you should be able to setup the boot order what goes first second and so on. If you select removable media as the first (provided your bios has that option) you sould be good to go.

 [/QUOTE]

I have no clue what cmos setup is. or how to even get into the bios onto this thing usually something pops up that says, i don't know, F10 gets you in, or something. not here...

I've not done any of this before...

[QUOTE=amohanty]

time consuming
loss of data
lack of information as to what went wrong which means you can repeat the problem.
e.g. I just completely borked my system while playing HL2 on cedega. Have no frigging idea but will probably spend a couple of days on it before even considering a reinstall. It may not be for everybody but it helps so that I dont do it again.

AM[/QUOTE]

not worried about time, except that i need a working computer by the 25th for school.
nor loss of data, as there IS no data on here except the botched kubuntu...
but understand the loss of info.
maybe it truly is something with the video card. but if so, i have no clue how to fix it. the instructions i've found are faaaar beyond my reach.

sigh. any of you in nyc and want to come do this for me? :-D

---

### Post by sarimalia on 2005-08-04
ok, so i dl-ed a live cd ISO on my friend's computer, burned it, but can't get the system to boot from it.

it was also recommended to try another live CD. someone named Mepis to me last night. so I did that. actually, couldn't tell if it was live or not, wasn't specified at download... but it still boots kubuntu, not whatever is on the CD. i figured with mepis, either i'd try and run something completely different, or it would reinstall and reformat everything and i'd see if another distro worked... but it just boots kubuntu.

why am i so inept?!

---

### Post by sarimalia on 2005-08-04
ok update... my friend's burning software is CRAP. i put nero on it, reburned live kubuntu... still doesnt work. my guess is plain old ubuntu would have the same problem.

tried a live mepis distro and it went on smooth. pictures clear as a bell. wireless went on right away. maybe that will be the way to go... hmmmm... the desktop wasn't my favorite though, i must say... 

any other recs/suggestions?

you guys have been amazing
sari

---

### Post by Hikaru79 on 2005-08-04
Sarmalia, do you have access to an IRC client anywhere on any computer? If so, come to channel #ubuntu on irc.freenode.net and message me, Hikaru79. I'll give you some live help, perhaps with SSH, if you contact me.

---

### Post by glowstick on 2005-08-04
Yea this happens to me too. After it finishes installing and everything it boots for the first time and begins setting up or something. And afterwards the screen just turns into multicolour blocks.

I downloaded the Kubuntu Live cd and it still has this problem after it finishes loading.

Can anyone suggest some other good linux distros?

---

### Post by Hikaru79 on 2005-08-04
[QUOTE=glowstick]Can anyone suggest some other good linux distros?[/QUOTE]
Woah, now, don't be hasty! What sounds like both of your problems might be is your monitor's refresh rates.

Guys, both of you paste the contents of your /etc/X11/xorg.conf file.

---

### Post by amohanty on 2005-08-05
> I have no clue what cmos setup is. 

When you boot the very first screen with all the mem tests and drive detection, at the very bottom of it it might say somethign like:

Press Del/F2 to enter Setup.

If you press the suggested key you will enter the CMOS setup.

HTH
AM

---

### Post by glowstick on 2005-08-06
I had this problem too, I have a Nvidia 6600 gt and I guess the nvidia drivers didnt work with the card because when I was configuring the display settings I chose the vesa driver instead and it worked perfectly.

---


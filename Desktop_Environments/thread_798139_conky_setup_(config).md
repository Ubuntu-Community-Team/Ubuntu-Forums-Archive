---
title: "conky setup (config)"
date: 2008-05-17
forum: Desktop Environments
---

### Post by TWeerts on 2008-05-17
i am trying to get conky to appear on my desktop under all the other windows. however, i cant even see it at all/ cant configure it either. it is installed, i used synaptic to install. when i open terminal to configure it, it gives me the space/spaces to configure it, but doesnt seem to do anything with that info. and conky still doesnt appear, any help?

---

### Post by kerry_s on 2008-05-17
in a terminal type: conky
if that works than conkys fine and working
now kill it: killall conky

to set up: cp /etc/conky/conky.conf ~/.conkyrc

conkyrc is where you put the settings, open it with a text editor:
editor ~/.conkyrc

now you probably asking yourself what are the settings? open a terminal and type: man conky
that's the manual.

---

### Post by EXCiD3 on 2008-05-17
Excellent source if you dont know where to start customizing, just copy someone elses and modify it for your own: [http://ubuntuforums.org/showthread.php?t=281865](http://ubuntuforums.org/showthread.php?t=281865)

---

### Post by TWeerts on 2008-05-18
when i type "comky" into the terminal, as i would to run it, it says "Conky: missing text block in configuration; exiting". conky doesnt even open

---

### Post by kerry_s on 2008-05-18
okay, sounds like a screwed install, try again.

[B]sudo apt-get remove --purge conky
sudo apt-get install conky[/B]

---

### Post by Nythain on 2008-05-18
its not a screwed install, they're missing the TEXT block in the rc file... my guess would be missing an rc file all together

cruise these forums, try copy/pasting a random .conkyrc or download one, throw it into your home folder then try loading conky again

---

### Post by kerry_s on 2008-05-18
> **Nythain said:**
> its not a screwed install, they're missing the TEXT block in the rc file... my guess would be missing an rc file all together

cruise these forums, try copy/pasting a random .conkyrc or download one, throw it into your home folder then try loading conky again

really, if it's not doing what it's suppose to do, i would say it was screwed. your not suppose to need a ~/.conkyrc for it to work, that's to customize it, if it can't even start normally, what other problems could it have? why take the chance?

---

### Post by EXCiD3 on 2008-05-18
> **kerry_s said:**
> really, if it's not doing what it's suppose to do, i would say it was screwed. your not suppose to need a ~/.conkyrc for it to work, that's to customize it, if it can't even start normally, what other problems could it have? why take the chance?

I agree that conky shouldnt need a .conkyrc to work. I installed and ran it without a configuration file and it worked fine. I think the purge and reinstall is a good idea, and think of it this way, its not going to hurt anything but cost him a few extra seconds at his computer, which isnt necessarily a bad thing either. :popcorn:

---

### Post by TWeerts on 2008-05-18
the purge worked. thanks alot. when i tried to install it the first time, i used synaptic. i guess it fowled up the install. i actually forgot about installing it from the terminal.

---

### Post by TWeerts on 2008-05-18
i now have conky running. however, i cant seem to make a .conkyrc file. what is the process for that?

---

### Post by signseeker on 2008-05-18
The .conkyrc file resides in your home directory. You can edit it with any text editor. 

Check out sourceforge for sample conky config files. They have screenshots and the config files which are used to create them on the site. 

Download/Copy one that you like and then save it in your home directory as .conkyrc. After that it's a matter of playing with the config file to make it look the way you want.

---

### Post by TWeerts on 2008-05-18
thats what i thought. i can copy and paste a config file into the editor, but when i go to save, it says the file doesnt exist.

---

### Post by signseeker on 2008-05-18
Hmm. Why not try nano -w .conkyrc (while in ur home directory) and then save the file. Once you create the file you should be able to edit it via another (prettier) editor.

---

### Post by TWeerts on 2008-05-18
ok, slow down. how do i get to my home directory?

---

### Post by signseeker on 2008-05-18
type cd /home/<username>

---

### Post by kerry_s on 2008-05-18
> **TWeerts said:**
> ok, slow down. how do i get to my home directory?

just type> cd
that is your home.
see post #2 if you are trying to copy the conkyrc file.

---

### Post by GarethEvans on 2008-06-07
I'm having the same "Conky: missing text block in configuration; exiting" issue, with an odd twist.  I found that if I log in as super user (su from a console) I can run conky just fine, however if I run it from my regular account or even using sudo it fails to start, with the same error message.  

I'm thinking the source of my problem is that I was an idiot and compiled as well as installed conky from source and then without thinking installed the package from the ubuntu repos, although they are the same version (1.5.1) so I really have no idea.  I did a "make uninstall" on the source that I had compiled followed by an "apt-get remove --purge conky" and that seemed to work fine but I'm still having the same issues upon reinstalling conky via apt.  Any ideas?

---

### Post by EXCiD3 on 2008-06-07
> **GarethEvans said:**
> I'm having the same "Conky: missing text block in configuration; exiting" issue, with an odd twist.  I found that if I log in as super user (su from a console) I can run conky just fine, however if I run it from my regular account or even using sudo it fails to start, with the same error message.  

I'm thinking the source of my problem is that I was an idiot and compiled as well as installed conky from source and then without thinking installed the package from the ubuntu repos, although they are the same version (1.5.1) so I really have no idea.  I did a "make uninstall" on the source that I had compiled followed by an "apt-get remove --purge conky" and that seemed to work fine but I'm still having the same issues upon reinstalling conky via apt.  Any ideas?

That usually means you have a misconfigured .conkyrc file. Can you post the output of this:```
cat ~/.conkyrc
```

I think running it as root looks for the root user's configuration file and yours is missing the block that starts with "TEXT". You could try copying and pasting a conkyrc config into yours and running conky then, or editing yours so that it has the TEXT section correctly. Look of other's configs for examples.

---

### Post by GarethEvans on 2008-06-08
Thanks for the quick reply. Actually right now I'm not using any conky config on my regular account and that still nets the same error.  I copied the default config from /etc/conky/ to ~/.conkyrc/ but that didn't do much either.

Here's the config (sans the large comment block at the beginning), just in case I'm missing something:

```
alignment bottom_left
background no
border_width 1
cpu_avg_samples 2
default_color white
default_outline_color white
default_shade_color white
draw_borders no
draw_graph_borders yes
draw_outline no
draw_shades no
font 6x10
gap_x 5
gap_y 60
minimum_size 5 5
net_avg_samples 2
no_buffers yes
out_to_console no
own_window yes
own_window_class Conky
own_window_type normal
stippled_borders 0
update_interval 3.0
uppercase no
use_spacer none

TEXT
$nodename - $sysname $kernel on $machine
$hr
${color grey}Uptime:$color $uptime
${color grey}Frequency (in MHz):$color $freq
${color grey}Frequency (in GHz):$color $freq_g
${color grey}RAM Usage:$color $mem/$memmax - $memperc% ${membar 4}
${color grey}Swap Usage:$color $swap/$swapmax - $swapperc% ${swapbar 4}
${color grey}CPU Usage:$color $cpu% ${cpubar 4}
${color grey}Processes:$color $processes  ${color grey}Running:$color $running_processes
$hr
${color grey}File systems:
 / $color${fs_free /}/${fs_size /} ${fs_bar 6 /}
${color grey}Networking:
Up:$color ${upspeed eth0} k/s${color grey} - Down:$color ${downspeed eth0} k/s
$hr
${color grey}Name                  PID   CPU%   MEM%
${color lightgrey} ${top name 1} ${top pid 1} ${top cpu 1} ${top mem 1}
${color lightgrey} ${top name 2} ${top pid 2} ${top cpu 2} ${top mem 2}
${color lightgrey} ${top name 3} ${top pid 3} ${top cpu 3} ${top mem 3}
${color lightgrey} ${top name 4} ${top pid 4} ${top cpu 4} ${top mem 4}

```

---

### Post by EXCiD3 on 2008-06-08
Well, it looks to me like there's absolutely nothing wrong...I wonder if your uninstalls left a file somewhere and is causing your problem. Try purging everything then running "locate conky" to see if there are any files/folders related to conky still on your system. Remove them, then do a reinstall. Hope that works.

---

### Post by vexingmodstwo on 2008-06-10
I've got a question about conky (and I didn't know where else to put this question and I didn't want to start a new thread)...

I have it installed and when I run it from the terminal it loads fine and displays fine but I never get my prompt back in the terminal.  Like something is hanging there.

Is this normal?  I'm assuming it isn't.  Here's what I see when I run "conky" in the terminal:

```

Conky: use_spacer should have an argument of left, right, or none.  'yes' seems to be some form of 'true', so defaulting to right.
Conky: can't load font 'arial'
Conky: desktop window (12000b4) is subwindow of root window (87)
Conky: window type - override
Conky: drawing to created window (3a00003)
Conky: drawing to double buffer



```

And that's it...  Blinking cursor and no command prompt.  I have to close the terminal if I want to do anything else.

---

### Post by EXCiD3 on 2008-06-10
Its running perfectly fine. When you run an application in terminal without a " &" after it...the application DEPENDS on terminal to still be there. If you run "conky &" then you will be presented with the prompt again. Without it, it waits until the application is finished executing.

---

### Post by vexingmodstwo on 2008-06-10
> **EXCiD3 said:**
> Its running perfectly fine. When you run an application in terminal without a " &" after it...the application DEPENDS on terminal to still be there. If you run "conky &" then you will be presented with the prompt again. Without it, it waits until the application is finished executing.

So you're saying I'm a noob?  ;)

Thanks!

---

### Post by EXCiD3 on 2008-06-11
> **vexingmodstwo said:**
> So you're saying I'm a noob?  ;)

Thanks!

exactly, couldnt have put that better myself :lolflag: jk i didnt know that until i started teaching myself python and reading through hundreds of tutorials just to learn stuff. at least you can admit it! ;) i would be rather be a linux noob than ANY sort of windows user :popcorn:

---

### Post by GarethEvans on 2008-06-11
> **EXCiD3 said:**
> Well, it looks to me like there's absolutely nothing wrong...I wonder if your uninstalls left a file somewhere and is causing your problem. Try purging everything then running "locate conky" to see if there are any files/folders related to conky still on your system. Remove them, then do a reinstall. Hope that works.

I just gave that a go and it worked.  There had been a couple files left over even after running apt-get with remove --purge. Thanks for that!

---

### Post by EXCiD3 on 2008-06-11
> **GarethEvans said:**
> I just gave that a go and it worked.  There had been a couple files left over even after running apt-get with remove --purge. Thanks for that!

Glad it worked! Sometimes there are files leftover that cause conflicts. They are probably created by the application and don't aren't tagged to be deleted when you do a remove or purge.

---

### Post by GarethEvans on 2008-06-11
I spoke too soon.  I've found that it runs fine as long as I have no .conkyrc folder in my home directory. I have no idea what would cause that. Permissions not being right on the folder maybe?

---

### Post by EXCiD3 on 2008-06-11
What errors does it give you when you run it in terminal? and post your conkyrc just in case its a problem with taht.

---

### Post by GarethEvans on 2008-06-11
The error is "Conky: missing text block in configuration; exiting".  The config I'm using is the default one, although I've tried a couple of different configurations (like blank files, cutting the comments out and a couple configs I found in threads), it doesn't seem to be an issue with the content. (at least from what I can see)

---

### Post by EXCiD3 on 2008-06-11
Huh, thats interesting. Since I don't know much about conky's internals probably your best bet would be to ask over at the Conky IRC channel: [#conky]("irc://irc.freenode.net/conky") on **irc.freenode.net**. Those guys should know everything you could possibly want to know about conky. ;)

---

### Post by GarethEvans on 2008-06-11
Thanks for the pointer

---

### Post by geezerone on 2008-06-24
I get the following message after installing from Synaptic or terminal and still happens after purging and reinstalling:

```
Conky: missing text block in configuration; exiting

```TIA

[U][B]EDIT: Solved, see below
[/B][/U]

---

### Post by geezerone on 2008-06-29
> **Nythain said:**
> its not a screwed install, they're missing the TEXT block in the rc file... my guess would be missing an rc file all together

cruise these forums, try copy/pasting a random .conkyrc or download one, throw it into your home folder then try loading conky again

Thanks, I found a conky.rc file with zero bytes in my Home folder. Configured this file with a working conky config and now working.

---

### Post by lengo on 2008-10-23
Wow! This is a really whacky (read 'conky') way to install / run a program . . . I installed from Synaptic Package Manager. Went to Terminal and typed conky; got an error. Found this thread; 'purged' conky; reinstalled conky with apt-get install conky. Went to Terminal and typed conky; got another error (Conky: missing text block in configuration; exiting). Purged / installed again; still getting the same error.

In /usr/share/doc/conky there is a 'readme.debian' file. It says, in part, that "it is *strongly* recommended that each user of "conky" create a configuration file in $HOME/.conkyrc based on the sample in /usr/share/doc/conky/examples/conky.conf.gz." I have tried extracting conky.conf.gz a number of times, but cannot find what it puts where (even with "Open destination folder after extracting" selected). How do I look at the example in conky.conf.gz? How do I give instructions to .conkyrc?!

Honestly, isn't there a better way . . . ? This is so frustrating.](*,)

---

### Post by Sorivenul on 2008-10-23
Look [HERE]("http://ubuntuforums.org/showthread.php?t=281865") on our own forums for some quick and easy ways to get started with .conkyrc files.  Lots of good stuff, and even pretty screenshots to go with some.  Sorry if this has already been posted.

---

### Post by Bruce M. on 2008-10-27
> **lengo said:**
> Honestly, isn't there a better way . . . ? This is so frustrating.](*,)

Check out my sig for the HowTo ...

Have a nice day.
Bruce

---

### Post by lengo on 2008-10-27
Thanks for the tutorial, Bruce. It looks like it would be useful if I could actually get past the second step (after downloading the package), i.e.:
> OK, so you have the file(s). Now to use conky, open a terminal and type:
```
conky
```
and you'll see a little window open and display a basic conky. That's the default conky found in: /etc/conky/conky.conf
Instead, as I indicated, when I type 'conky' in Terminal I get the error:
```
Conky: missing text block in configuration; exiting
```
Your tutorial doesn't address this . . . :confused:

---

### Post by Bruce M. on 2008-10-27
> **lengo said:**
> Thanks for the tutorial, Bruce. It looks like it would be useful if I could actually get past the second step (after downloading the package), i.e.:

Instead, as I indicated, when I type 'conky' in Terminal I get the error:
```
Conky: missing text block in configuration; exiting
```
Your tutorial doesn't address this . . . :confused:

Do you use "Mark for complete removal" when removing it?

Maybe you have an orphaned file somewhere. Check in Synaptic > Custom Filters > Orphaned.

---

### Post by lengo on 2008-10-28
> **Bruce M. said:**
> Do you use "Mark for complete removal" when removing it?

Maybe you have an orphaned file somewhere. Check in Synaptic > Custom Filters > Orphaned.
No, I used "sudo apt-get remove --purge conky" in a command line (as per instructions in post #5 [here]("http://ubuntuforums.org/showthread.php?t=798139"))

As for an "Orphaned" file, is that the same as "Broken"? Because in Synaptic > Custom Filters I have: All, Broken, Community Supported, Marked Changes, Package with Debconf, Search Filter, and Upgradable but not Orphaned . . .

---

### Post by Bruce M. on 2008-10-28
> **lengo said:**
> No, I used "sudo apt-get remove --purge conky" in a command line (as per instructions in post #5 [here]("http://ubuntuforums.org/showthread.php?t=798139"))

As for an "Orphaned" file, is that the same as "Broken"? Because in Synaptic > Custom Filters I have: All, Broken, Community Supported, Marked Changes, Package with Debconf, Search Filter, and Upgradable but not Orphaned . . .

Good News: That means you don't have an orphaned file. If you did it would be there.

OK, so you did the purge (I was looking a Kerry_s's post just before coming here).

OK, do an install and then look for:
```
/etc/conky/conky.conf
```
to see if it exists.

At least that way we know it is installed.

Now try this:

Create a directory: ~/Conky and in there put this file called **conkymain** so you'll have ~/Conky/conkymain
```

alignment bottom_left
background no
border_width 1
cpu_avg_samples 2
default_color white
default_outline_color white
default_shade_color white
draw_borders no
draw_graph_borders yes
draw_outline no
draw_shades no
font 6x10
gap_x 5
gap_y 60
minimum_size 5 5
net_avg_samples 2
no_buffers yes
out_to_console no
own_window yes
own_window_class Conky
own_window_type normal
stippled_borders 0
update_interval 3.0
uppercase no
use_spacer none

TEXT
$nodename - $sysname $kernel on $machine
$hr
${color grey}Uptime:$color $uptime
${color grey}Frequency (in MHz):$color $freq
${color grey}Frequency (in GHz):$color $freq_g
${color grey}RAM Usage:$color $mem/$memmax - $memperc% ${membar 4}
${color grey}Swap Usage:$color $swap/$swapmax - $swapperc% ${swapbar 4}
${color grey}CPU Usage:$color $cpu% ${cpubar 4}
${color grey}Processes:$color $processes  ${color grey}Running:$color $running_processes
$hr
${color grey}File systems:
 / $color${fs_free /}/${fs_size /} ${fs_bar 6 /}
${color grey}Networking:
Up:$color ${upspeed eth0} k/s${color grey} - Down:$color ${downspeed eth0} k/s
$hr
${color grey}Name                  PID   CPU%   MEM%
${color lightgrey} ${top name 1} ${top pid 1} ${top cpu 1} ${top mem 1}
${color lightgrey} ${top name 2} ${top pid 2} ${top cpu 2} ${top mem 2}
${color lightgrey} ${top name 3} ${top pid 3} ${top cpu 3} ${top mem 3}
${color lightgrey} ${top name 4} ${top pid 4} ${top cpu 4} ${top mem 4}
```

Now in terminal type:
```
conky -c ~/Conky/conkymain &
```
you should see it on your screen.

Let me know how it works.

BTW: The "conkymain" I gave you is a copy of my /etc/conky/conky.config

CHIMO!
Bruce

---

### Post by lengo on 2008-10-28
> **Bruce M. said:**
> OK, do an install and then look for:
```
/etc/conky/conky.conf
```
to see if it exists.
It exists; /etc/conky/conky.conf is 2.4 KB.
> **Bruce M. said:**
> Now try this: Create a directory: ~/Conky and in there put this file called **conkymain** so you'll have ~/Conky/conkymain.
I tried "mkdir" in terminal and got "Permission denied". I tried creating a file in Nautilus (that's the file explorer, right?), with File > Create folder, but it's greyed out . . . So I'm stuck. And is ~/Conky in my "home" folder, "root" folder, "any" folder I choose? And why do I have to do this if Conky is already installed in /etc/conky/conky.conf (obviously, I could copy my own conky.conf to another location, but what's the point?)? This is what I mean when I say I find this so frustrating . . . I install a program; I have determined that it exists and that it is not orphaned; it does not run; I do not have permission to create a directory to complete the helpful instructions I'm given; I do not know where ~/ is . . . I'm here to learn--I'm not interested in MAC and am tired of MS--but the curve is steep some times!

---

### Post by Bruce M. on 2008-10-28
> **lengo said:**
> It exists; /etc/conky/conky.conf is 2.4 KB.

I tried "mkdir" in terminal and got "Permission denied". I tried creating a file in Nautilus (that's the file explorer, right?), with File > Create folder, but it's greyed out . . . So I'm stuck. And is ~/Conky in my "home" folder, "root" folder, "any" folder I choose? And why do I have to do this if Conky is already installed in /etc/conky/conky.conf (obviously, I could copy my own conky.conf to another location, but what's the point?)? This is what I mean when I say I find this so frustrating . . . I install a program; I have determined that it exists and that it is not orphaned; it does not run; I do not have permission to create a directory to complete the helpful instructions I'm given; I do not know where ~/ is . . . I'm here to learn--I'm not interested in MAC and am tired of MS--but the curve is steep some times!

~/ is a shortcut for: /home/username/

on my PC: ~/ is equal to: /home/bruloo/

OK, no, it is not "necessary" to put it in ~/Conky, but keeps conky where you can see it. You can put it anywhere and call it anything you want.

To start it you'd need to:

```
conky -c ~/folder_if_any/filemane &
```
or
```
conky -c ~/.myconkyfile &
```
if you want it hidden

Strange you can't make a folder.

Right click on the folder and check the permissions (see attached)

Chimo!
Bruce

---

### Post by lengo on 2008-10-28
I had been trying to make a directory in 'root'; that's what I thought ~/ was . . . That would explain why I couldn't create a folder. Oops. I followed your directions in my /home/paul folder and I get Conky to run. Yay! But my terminal looks 'hung'; it doesn't return to "paul@####:~$". Should I be worried about that? And should I leave Conky in my /home/paul folder? And any idea why it doesn't work in /etc?

Now to learn how to configure Conky. Some things I'd like (if you could help me with this part of setup? or should I start a new thread?): always on top; transparent; temperatures (CPU, GPU); fan speed . . .

Thanks for getting me going!

---

### Post by Bruce M. on 2008-10-28
> **lengo said:**
> I had been trying to make a directory in 'root'; that's what I thought ~/ was . . . That would explain why I couldn't create a folder. Oops. I followed your directions in my /home/paul folder and I get Conky to run. Yay! But my terminal looks 'hung'; it doesn't return to "paul@####:~$". Should I be worried about that? And should I leave Conky in my /home/paul folder? And any idea why it doesn't work in /etc?

Now to learn how to configure Conky. Some things I'd like (if you could help me with this part of setup? or should I start a new thread?): always on top; transparent; temperatures (CPU, GPU); fan speed . . .

Thanks for getting me going!

/etc is owned by root.

Note for future reference: 

**[SIZE="5"]/[/SIZE]** is root
**[SIZE="5"]~/[/SIZE]** is a shorcut for /home/paul/

I really should have explained that more clearly, sorry about that.

:lolflag: do what most of us did!  Steal ...errrr... "*Borrow*" one from [here (linked to the last page to get the newer stuff)]("http://ubuntuforums.org/showthread.php?t=281865&page=426") that you like and "tweak" it to your system.

No need to start a new thread we are here to help you.

For example if you want CPU, GPU HD temperatures and such you'll need lm-sensors.  Check out my HowTo again, it's explained in there and some other goodies you might want.

As for your terminal, if you close it does conky stay running?
Sometimes mine doesn't return to the prompt either. Just type a new command it will work. Try this one:
```
clear
```
it simply clears the screen, you can still scroll up to see what was there.

Chimo!
Bruce

---

### Post by Alektrotsky on 2009-02-26
Hiya. I was wondering if there was any way to add a 'button' to my Conky that I could click on, that would open my browser and travel automatically to a particular URL (say-- Gmail). It already tells me if I have any new mail... I'm just lazy and want to have it take me to that mail automatically.

---

### Post by Bruce M. on 2009-02-27
> **Alektrotsky said:**
> Hiya. I was wondering if there was any way to add a 'button' to my Conky that I could click on, that would open my browser and travel automatically to a particular URL (say-- Gmail). It already tells me if I have any new mail... I'm just lazy and want to have it take me to that mail automatically.

No, but you can get: [Conky SSL Email Python Script]("http://ubuntuforums.org/showthread.php?t=869771") that will do that and a LOT more for you.

Have a nice day.
Bruce

---

### Post by dfmalh on 2009-04-21
Hi, I cant seem to get this code to work... I have two flash drives DM_1GB and DM_8GM. I want to display the amount of space avalible on each drive when either or both are pluged in and or "No external storage detected." if both are unpluged.

What is happening at the moment, only the DM_8G is working properly, when I plug it in and unmount it. If I plug the DM_1G drive in, it shows up, but everything that is displayed (output) below that (code for network stuff) disappear... it reappear when I unplug/mount the drive...

I am sure it has something to do with the "if_mounted" and "endif" commands, but I can't get my head around it... Help!

Here is the:

```

STORAGE (Other) ${hr 2}
${if_mounted /media/DM_1GB}DM_1GB have ${fs_free /media/DM_1GB}avalible.${else}
${if_mounted /media/DM_8GB}DM_8GB have ${fs_free /media/DM_8GB}avalible.${else}
No external storage detected${endif}



```

---

### Post by VCoolio on 2009-04-21
You start if_mounted twice, but there is only one endif. Try closing the line for DM_1GB with endif also.

---

### Post by dfmalh on 2009-04-22
Hi VCoolio, thanks for the sugestion, but that also doesn't work, in fact conky doesn't even start. If I add another "endif" this is the output:

> Conky: statfs '/media/DM_1GB': No such file or directory
Conky: statfs '/media/DM_8GB': No such file or directory
Conky: $else: no matching $if_*


---

### Post by VCoolio on 2009-04-22
The messages ("No such file or directory") indicate that the media are not mounted or you pointed to the wrong media. At least, that's what I get when my external hdd is not running. Check the exact names on your drives in the /media folder. 
About the $else I'm not sure. Try posting your question in the huge conky thread [here]("http://ubuntuforums.org/showthread.php?t=281865"), more people will read that.
Hope that helps.

---

### Post by dfmalh on 2009-04-23
Hi VCoolio,

Thanks, I checked the names and paths, everything is correct. I will post on the other thread and see what happens.

Thanks again for your help.

---


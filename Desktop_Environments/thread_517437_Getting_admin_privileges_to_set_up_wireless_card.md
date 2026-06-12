---
title: "Getting admin privileges to set up wireless card"
date: 2007-08-04
forum: Desktop Environments
---

### Post by billw11 on 2007-08-04
i cant make any changes at all with unbuntu because it keeps telling me no administrative privelges to edit files....
what i would like is no user sign on at ALL with full privleges..
is there a setup im missing that will give me full undenied access and
be able to shut down and start up without signing on???

im new to unbuntu and id like to be able to have full access like windows as im the only one that uses this computer

---

### Post by AndyCooll on 2007-08-04
Ubuntu uses sudo to gain admin rights, e.g. from the command line: sudo gedit /etc/apt/sources.list or gksudo nautilus.

Both of the above will open the relevent apps and files in admin mode. Users starting in non-admin mode is there to prevent you inadvertantly borking your system.

See here for more information: [RootSudo]("https://help.ubuntu.com/community/RootSudo")

:cool:

---

### Post by nichipet on 2007-08-04
From what I gather, it sounds like you are trying to access programs or files that require root access. On Ubuntu, the root user is disabled (basically), and you use the following to access root programs/files:

```
sudo gedit <file>
```

I'm not sure about disabling the password check entirely, but I know it can be tweaked. When you enter the above command it will say

> Password:

and you enter your password. If you have administrator privileges, you will then have full access for a set period of time.

---

### Post by billw11 on 2007-08-04
also, id like to add that i cant get internet access until i gain admin privleges, so i have to keep switching back to windows because unbuntu wont let me setup my wireless connection without admin priv.

im willing to give unbuntu a chance, but if i cant do anything without admin. rights, ill just stay with windows and reclaim the hard drive space.

any help appreciated

---

### Post by aysiu on 2007-08-04
This should help:
[http://www.psychocats.net/ubuntu/permissions#gui](http://www.psychocats.net/ubuntu/permissions#gui)

And don't use *sudo gedit*. Use *gksudo gedit* instead.
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by merlinus on 2007-08-04
You can try adding yourself to the admin group (and perhaps others as well) to see if that helps.

System/Administration/Users and Groups.

-merlin

---

### Post by aysiu on 2007-08-04
> **billw11 said:**
> also, id like to add that i cant get internet access until i gain admin privleges, so i have to keep switching back to windows because unbuntu wont let me setup my wireless connection without admin priv.

im willing to give unbuntu a chance, but if i cant do anything without admin. rights, ill just stay with windows and reclaim the hard drive space.

any help appreciated
Well, why don't we focus on the real problem. What kind of internet connection are you trying to get working? USB modem? Dial-up modem? Wireless? Can you also mention what brand of modem/card you're using?

---

### Post by nichipet on 2007-08-04
Assuming you're in Gnome, and I'm not in Linux right now so this may not be completely correct, go into System:Preferences:Users and Groups  It may not be Preferences, if it's not, try the other choice (there's only two).

Edit or View Properties, something along those lines, for your username. You should see, I believe it may be in an Advanced tab, a checkbox for being able to administer the system. If it's checked, you already have the access. Try a command such as the ones suggested from the Terminal (Applications:Accessories:Terminal) and when asked for a password, give the one you use to log in.

That should work.

---

### Post by aysiu on 2007-08-04
> **merlinus said:**
> You can try adding yourself to the admin group (and perhaps others as well) to see if that helps.

System/Administration/Users and Groups.

-merlin
The first user created during installation is already put of the *admin* group. But administrative privileges for particular tasks can be invoked only with the use of *sudo*, *gksudo*, or *kdesu*.

---

### Post by billw11 on 2007-08-04
im using a linksys wusb54g  usb 54g wireless adapter.
the wireless unit im receiving signal from is also linksys 54g
there are no passwords needed on the setup.
windows sees it and connects immediately at 54g.

but unbuntu sees the signal @ 54g
but claims its only 11mb receiver and wont connect to signal.
i cant make changes to admin policies as everytime i make the changes it reverts right back to user status with no rights.

im sorry for the frustration, but im used to being anle to setup O/S
to automatically log on as administrater without a log on screen.
i dont care about viruses or people hacking my computer as i back things up onto dvd.
i just need internet running as its hard to learn this when switching between O/S's

---

### Post by aysiu on 2007-08-04
Your wireless card isn't natively compatible with Ubuntu. It has closed source drivers that are made for only Windows.

Luckily for you, there is a workaround. You can use something called *ndiswrapper* to use the Windows drivers non-natively. [This post has a solution](http://ubuntuforums.org/showpost.php?p=2874915&postcount=1).

**Edit**: Now that I take a second look at the instructions, they're a bit cryptic for a new user. So I'm going to attempt to translate them for you.

1. Download [this file](http://easynews.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.47.tar.gz) and transfer it to your Ubuntu computer's desktop.

2. In [the terminal](http://www.psychocats.net/ubuntu/terminal), type ```
cd ~/Desktop
tar -xvzf ndiswrapper-1.47.tar.gz
cd ndiswrapper-1.47
make distclean
make
sudo make install
``` When prompted for your password, enter your password. [You won't see any visual feedback, but your password is still being accepted.](http://www.psychocats.net/ubuntu/passwordinterminal)

3. Grab latest driver from [linksys]("http://www.linksys.com/servlet/Satellite?c=L_CASupport_C2&childpagename=US%2FLayout&cid=1166859843775&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=4377540888B29&displaypage=download#versiondetail").

4. Unzip that driver and move it to the Ubuntu computer. Find the WUSB54Gv4 directory. It'll probably be something like ```
cd ~/Desktop/WUSB54Gv4
```

5. ```
ndiswrapper -v
``` Make sure there are no errors.

6. ```
ndiswrapper -i rt2500usb.inf
sudo depmod -a
sudo modprobe ndiswrapper
```

7. ```
ndiswrapper -l
``` may show an alternative driver (rt2570)

8. Blacklist the driver by running ```
gksudo gedit /etc/modprobe.d/blacklist
``` and adding ```
blacklist rt2570
``` to the end.

9. ```
gksudo gedit /etc/modprobe.d/ndiswrapper
``` change ```
wlan0
``` to ```
rausb1
```

10. Reboot

---

### Post by billw11 on 2007-08-04
while im asking questions , and to simplify this ,
is there any way to permanently log on as administrator , not as user ,
it boggles my mind that i need my own permission to access any file on the computer.
i want to learn this but not get frustrated logging back and forth

---

### Post by billw11 on 2007-08-04
thank you for the simplified explanation, i did run accross this same solution , but thats where my troubles get worse.
ive partioned off a blank 80 gig drive to let unbuntu reside soley on.
ive reinstalled unbuntu twice , both times produced exact same results.
neither time will it allow me to just install without creating a user.
after install both times, i go into blacklist file to blacklist installed driver for wireless , and i proceed to save the file (replace file save) 
both times exactly same results , i dont have permissions to edit file.

i go into user groups to give myself admin priveleges and put myself on admin or root group , always it refuses to  keep me in that group.
it reverts me back to user  and says i dont have permission to alter files again. even after rebooting after changes...

im beggining to wonder should i consider a different version of linux???
this is getting frustrating

---

### Post by billw11 on 2007-08-04
also , i cant install anything at all because of no permissions...
is this just a look at me version of unbuntu ???

---

### Post by billw11 on 2007-08-04
ok, i think ive the answer.
thanks for the help everyone
back to windows

---

### Post by billw11 on 2007-08-05
1 final time before i format unbuntu into ntfs.
i go into user groups and try setting my name as admin or root group to give myself full rights , but it always reverts back and wont let me make any file changes to anything , or install anything.

what gives ????

how do i get around this so i can actually do anything at all on unbuntu.

do i reinstall and import settings from windows xp ???

---

### Post by aysiu on 2007-08-05
Ubuntu isn't being stubborn. You're just not actually learning how to use it.

Read this page:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

I promise--it won't hurt. Read it.

---

### Post by kirios on 2007-08-05
[http://ubuntuforums.org/showpost.php?p=3134474&postcount=15]("http://ubuntuforums.org/showpost.php?p=3134474&postcount=15")
[COLOR="DarkRed"]Don't switch back to Vista - you'll need administrator privileges for nearly everything you do (including emptying the Recycle Bin). :-) 
If you just want a GUI login as the root user (not recommended), try PCLinuxOS.[/COLOR] 
[http://distrowatch.com/table.php?distribution=pclinuxos]("http://distrowatch.com/table.php?distribution=pclinuxos") 
[COLOR="DarkRed"]And don't forget to visit this page: [/COLOR]
[http://distrowatch.com/stats.php?section=popularity]("http://distrowatch.com/stats.php?section=popularity") 
[COLOR="DarkRed"]lol[/COLOR]

---

### Post by ugm6hr on 2007-08-05
To open files to edit - use command gksudo:
```
gksudo nautilus
```

This will allow you access to any files you want (after you retype your password).

The reason for restricted access is to ensure you don't accidentally delete important system files.

As for your wifi USB - there are 4 versions of your card - so make sure it's the right one:
```
lsusb -v
```
And compare the usbid to those listed here: [http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_g-l/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_g-l/) (you can use Ctrl+F in Firefox)

If it's definitely a v4 - then carry on with the prior advice.  Otherwose ask again (after posting the version number / usbid).

---

### Post by aysiu on 2007-08-05
> **kirios said:**
> 
If you just want a GUI login as the root user (not recommended), try PCLinuxOS. Well, you **can** get a graphical root login in Ubuntu. It's just not *necessary*.

The OP should understand there may be better ways to do things than to log in as root graphically. And the alternatives can still be point-and-click solutions like a ```
gksudo nautilus
``` launcher.

---

### Post by billw11 on 2007-08-05
am i going to have to do this every single time???
will this be needed once or will i need to run this for everything i save, install , modify .???
if so , is there no true bypass?
 
i learned windows by search & destroy.
id like the same with linux, 

thanks for all the help, please understand my frustration as this is taking an extremely long time just to get an internet connection as i have to keep switching back to windows to get help. 
wheres the logic in that if windows is the reliable o/s

---

### Post by ugm6hr on 2007-08-05
Why don't you try and fix your wifi (or see if it is possible to fix).

This advice in your other thread:
[http://ubuntuforums.org/showpost.php?p=3136458&postcount=16](http://ubuntuforums.org/showpost.php?p=3136458&postcount=16)

You do not need to keep typing anything - create a custom panel launcher with the command *gksudo nautilus*.  That way you will just have to click on it, enter the password when asked, and you have full access until you choose to close the window.

"Search & destroy" may have worked in Windows, and it can in Ubuntu too ;)  But it is better to be pre-warned that you might be heading towards the *destruction* phase....

---

### Post by billw11 on 2007-08-05
thanks all for the patience with me.

ive been trying to fix my wifi problem for 3 days now with no luck at all.
everytime i try to edit the file to blacklist my adapter, im told i dont have permissions to do so.
everytime i try to grant myself permission to edit files, it reverts back to not allowing me to make the changes.

its a never ending conundrum of not being allowed to add hardware or software because of permissions...

while im writing this , which is better , ubuntu or kubuntu ???
and can i just format my e drive into straight ntfs and install ubuntu onto it instead of creating a non recognized drive by windows

---

### Post by ugm6hr on 2007-08-05
> ive been trying to fix my wifi problem for 3 days now with no luck at all.
everytime i try to edit the file to blacklist my adapter, im told i dont have permissions to do so.
everytime i try to grant myself permission to edit files, it reverts back to not allowing me to make the changes.
How do you open the blacklist file?  You do not need to change any permissions at all.  

When you open the blacklist file - either use *gksudo nautilus* to browse to the file and double-click - or use *gksudo gedit /etc/modprobe.d/blacklist* - to open it and you will be able to save it with no problem.

> while im writing this , which is better , ubuntu or kubuntu ???
It's about personal preference.  If you don't know what you're doing, it is easier to use Ubuntu, because the vast majority of the information on this forum relates to Ubuntu (although is transferable to Kubuntu with a bit of knowledge).

> and can i just format my e drive into straight ntfs and install ubuntu onto it instead of creating a non recognized drive by windows
No. If you want to recognise the partition in Windows - install ext2fs in Windows: [http://www.fs-driver.org/](http://www.fs-driver.org/)

PS: I am assuming that you installed Ubuntu yourself, and have not created any additional users (or modified the original user's settings).  If this is not true - then you will have to log in with an administrator's username.

---

### Post by billw11 on 2007-08-05
and yes, for me its neccessary to always be able to install or edit anything at any time.
its my mindset that its my computer , i dont need my own permission.
just like sitting down , nobody asks themselves for permission to stand up.
ive learned 1 very valuable thing from windows.
it takes me 2 hours to format & reinstall everything on xp including software.everything is saved on dvds or accross 3 hard drives on 1.1 terrabytes of space with 1 more sata hookup for a planned terrabyte HD

ive spent days trying to repair files before , and have realized why fix when reinstall and learn from mistake is faster and easier.

thats my frustration. let me make the mistakes so i can learn from them.
without the permissions set , theres nothing i can do with ubuntu.
it wont even let me watch a DVD because it requires a codec that requires permissions to install](*,)](*,)

---

### Post by ugm6hr on 2007-08-05
> **billw11 said:**
> thats my frustration. let me make the mistakes so i can learn from them.
without the permissions set , theres nothing i can do with ubuntu.
it wont even let me watch a DVD because it requires a codec that requires permissions to install

In the modern world - I believe even Vista asks for authorisation for any system activity - because of concerns regarding security.

So be prepared for years of frustration!

---

### Post by kirios on 2007-08-05
**billw11 wrote**> for me its neccessary to always be able to install or edit anything at any time.
its my mindset that its my computer , i dont need my own permission.... it wont even let me watch a DVD because it requires a codec that requires permissions to install
[COLOR="Red"]From [/COLOR][https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo"): 
>  "The benefits of leaving root logins disabled by default include the following:

    *       The installer has to ask fewer questions.
    *      Users don't have to remember an extra password (i.e. the root password), which they are likely to forget.
    *      It avoids the "I can do anything" interactive login by default (e.g. the tendency by users to login as an "Administrator" user in Microsoft Windows systems), you will be prompted for a password before major changes can happen, which should make you think about the consequences of what you are doing.
    *      Sudo adds a log entry of the command(s) run (In /var/log/auth.log). If you mess up, you can always go back and see what commands were run. It is also nice for auditing.
    *      Every cracker trying to brute-force their way into your box will know it has an account named root and will try that first. What they don't know is what the usernames of your other users are. Since the root account password is locked, this attack becomes essentially meaningless, since there is no password to crack or guess in the first place.
    *      Allows easy transfer for admin rights, in a short term or long term period, by adding and removing users from groups, while not compromising the root account.
    *      sudo can be setup with a much more fine-grained security policy.
    *      The authentication automatically expires after a short time (which can be set to as little as desired or 0); so if you walk away from the terminal after running commands as root using sudo, you will not be leaving a root terminal open indefinitely."


---

### Post by aysiu on 2007-08-05
I've merged these two threads, because the two issues are related. The OP believes getting admin privileges will help with setting up wireless. Setting up the wireless card is the ultimate goal. The "let me do anything with no restrictions" request is what the OP believes is necessary to get to that ultimate goal.

---

### Post by nichipet on 2007-08-05
Personally, I find it a bit ironic that following the instructions offered, giving information requested, and getting the wireless fixed would have been finished a while ago and administrator access for wireless would be a moot issue by now.

We can debate administrator access for years, and yes, billw11, you may want to consider another distribution of Linux which does allow you to log in as root (without a hack like in Ubuntu), but for now we can refocus on getting wireless to work.

If so, how about we restart with going through the commands people offered, wanting output to help diagnose the problem, give us the outputs, and specifications of the wireless card. From there, we can look into the wireless problem and try to fix it.

---

### Post by billw11 on 2007-08-06
this is getting too much for me.
ive got ndiswrapper  sitting on my desktop now...
what am i suppossed to do with it ????
do i install it & how do i install it ???
i figured out i can drag n drop files onto it , but then what???
ive finnally blacklisted usb modem. now what?
open file & enter code ? where?
do i open a terminal to enter code? do i hit enter after every line like DOS ?
please , im switching back and forth between windows just to get an internet connection to get help.
it took me 15 minutes to install usb modem into windows from opening box to having a connection.
almost 3 days now for ubuntu for no connection.

tommorow is my last try to get this.
NO i cant plug in an ethernet cable. a custom made 200 foot cable isnt worth it.
ive no more patience today, ill try 1 more time in the morning before reclaiming the hard drive for windows.

---

### Post by babysteps on 2007-08-06
> **billw11 said:**
> this is getting too much for me.
ive got ndiswrapper  sitting on my desktop now...
what am i suppossed to do with it ????
do i install it & how do i install it ???
i figured out i can drag n drop files onto it , but then what???
ive finnally blacklisted usb modem. now what?
open file & enter code ? where?
do i open a terminal to enter code? do i hit enter after every line like DOS ?
please , im switching back and forth between windows just to get an internet connection to get help.
it took me 15 minutes to install usb modem into windows from opening box to having a connection.
almost 3 days now for ubuntu for no connection.

tommorow is my last try to get this.
NO i cant plug in an ethernet cable. a custom made 200 foot cable isnt worth it.
ive no more patience today, ill try 1 more time in the morning before reclaiming the hard drive for windows.

First of all, I just saw your post today. I'm not sure why no one else has said it (maybe it's something we shouldn't do, but it really does get things moving!), but for me, when even "sudo" doesn't get me the permission, or when it tells me I don't have "Supercow" power, I type "sudo -s", then wait for the prompt to turn into  "root@(Your hostname).  Then I can usually issue the  any command  I want. This is especially true when I try to follow instruction that involves "echo....".  Hope that helps you. 

With Ndiswrapper is it a file that ends in .gz ? If so you will want to move it and untar it.  

As a noobie myself  I can say that you will need to know how to move (mv) or copy (cp) files from one place to another. 
It will also help to know how to change directory (cd) and know the spacing when you type in the terminal. 
Also, know that it makes a difference whether something is capitalized or not. 
 Another thing that helps eliminate typing error is to know how to use the Tab key.  If you're typing a filename midway, and you hit Tab, the computer will finish it for you (if you're on the right track), or at least supply up to the part where it may be different. (for example up to the part before the .inf, or .sys)

I feel for you, but i hope you give it more time. You will need a lot of time and patience.  Myself I took the plunge in April with two crippled  laptops.  I installed Ubuntu on both of them.  The Acer miraculously got online at the end of the 1st day.  The Compaq? As a matter of fact, I JUST (one hour ago)  got it to go online (!) which is about 4 months later. 

Windows may appear to be quick and easy, but it's a walking time bomb, and there's no real interaction.  Ubuntu isn't that kind of a machine. There will be nothing but frustration if you just want Ubuntu to be something it isn't.  In which case maybe it's better to come back to ubuntu when you have more time and patience. 

Good luck to you!

Babysteps

---

### Post by billw11 on 2007-08-06
im using xp, not vista. ive seen vista and refuse to use it until i have a quad or 8 core  amd machine. bad enough ive got a crummy intel.

but for now , i just want internet connection. ive finally blacklisted wireless. now how do i install modem. ndiswrapper 1.8 sitting on desktop.
i have modem cd right here no need for downloading newer driver.

i think ill just buy xp pro 64  because i dont want to deal with possible problems on a quad or 8 core machine.
i cant get connection by tomorrow , ill give up.
i couldve reformatted windows 3 times in the time its taken me trying to learn this.

at least ive learned to never consider an imac

---

### Post by ugm6hr on 2007-08-06
> **billw11 said:**
> this is getting too much for me.
ive got ndiswrapper  sitting on my desktop now...
what am i suppossed to do with it ????
do i install it & how do i install it ???
i figured out i can drag n drop files onto it , but then what???
ive finnally blacklisted usb modem. now what?
open file & enter code ? where?
do i open a terminal to enter code? do i hit enter after every line like DOS ?
please , im switching back and forth between windows just to get an internet connection to get help.
it took me 15 minutes to install usb modem into windows from opening box to having a connection.
almost 3 days now for ubuntu for no connection.

tommorow is my last try to get this.
NO i cant plug in an ethernet cable. a custom made 200 foot cable isnt worth it.
ive no more patience today, ill try 1 more time in the morning before reclaiming the hard drive for windows.

Unfortunately, your frustration is a result of not having internet on Ubuntu, and not having access to a second computer with internet access to use at the same time as setting up Ubuntu.

Bear with me - I think I have some useful suggestions for you.

First - I would suggest you read aysiu's website ([http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)) - it will clear up some of your misconceptions that you have carried over from Windows.  Unfortunately for you, Ubuntu is not *that* similar to Windows, and is not really designed for ease of transfer.  It is designed to be as easy to use for *all* people (not just those from Windows).  If this is a major hold-up for you, then perhaps the PCLinuxOS ([http://www.pclinuxos.com/](http://www.pclinuxos.com/)) suggestion is not bad - you may feel more at home with it.  However, I think they extra effort now will reap benefits in the long term with Ubuntu (I was a Windows user too - and have been happily using Ubuntu for almost 6 months now - but I have been reading on this forum for over a year now).

So that you can feedback useful information to us (so we can see where you're going wrong), it would be helpful if you can access the files on your Ubuntu partition from Windows.  To achieve this - download and install the Ext2fs program from [http://www.fs-driver.org/](http://www.fs-driver.org/) *in Windows*.  This way, you can copy the "Terminal" entries and outputs from Terminal into a text editor or word processor (you have OpenOffice installed), and save it as a Word (.doc) file you can read in Windows - and then cut and paste back into this forum.  It is very hard to help without knowing *exactly* what you have done.  

Also - you can *already* access your Windows drive from Ubuntu.  So make sure you save all relevant webpages here on your HD - and then find and open them from Ubuntu for reference (so you can cut and paste commands into Terminal - spelling errors will make a mess of it!!!!)

Having done this, it would be helpful to confirm your hardware before going any further.  Post the result from the command (and YES - you do press Enter after each line):
```
lsusb -v
```
Having done this, use the technique above to give us the results.  This advice still stands:
[http://ubuntuforums.org/showpost.php?p=3136458&postcount=19](http://ubuntuforums.org/showpost.php?p=3136458&postcount=19)

Having confirmed your hardware (which we can do with the results from above) - hopefully, the previously posted solution will in fact be correct:
[http://ubuntuforums.org/showpost.php?p=3133335&postcount=11](http://ubuntuforums.org/showpost.php?p=3133335&postcount=11)
If so - then again - start from the beginning - and when you run into problems - post back with the output from Terminal.

Hopefully this will stop the endless to-ing and fro-ing between OS.

I sincerely hope you get this fixed so that you can start to actually enjoy the benefits of Ubuntu in the near future.... but be prepared for a bit more learning before you are 100% comfortable with it.  Thankfully, it's a *lot* easier to learn with a live internet connection :)

---

### Post by billw11 on 2007-08-06
actually , i wanted ubuntu for 2 reasons.
1. i wanted a 2nd O/S installed for when i crash windows. the crashes arent due to viruses , my overloading it with too many demands.
burn a dvd while downloading while searching internet. i rarely have resources left. i just wanted to be able to copy my settings before formatting for fresh install.

2. i wanted to compare ubuntu to windows and experiment with it.

but my experiment is almost over.im tired. windows pro 64 is looking really good right now. i guess i can  install win pro & use xp as secondary O/S.
i dont have vista, but neighbor does. i dont like vista but nobody considers it was developed for a quad and 8 core machine.

my next machine will have a native DVI  output  hopefully 8 core.
ubuntu doesnt recognize my dvi on a dual core, and no internet.

i really wanted to give ubuntu a chance, but no internet and im still relling on windows.
SIGH

---

### Post by kirios on 2007-08-06
> **billw11 said:**
> ... i couldve reformatted windows 3 times in the time its taken me trying to learn this.

at least ive learned to never consider an imac
[COLOR="DarkRed"]Why not? An iMac gives you OS X, no hardware incompatibilities and even the ability to dual-boot Windows - not too sure why anyone would want to do that though![/COLOR]

---


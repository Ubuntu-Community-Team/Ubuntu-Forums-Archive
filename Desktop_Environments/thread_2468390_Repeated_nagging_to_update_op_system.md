---
title: "Repeated nagging to update op system"
date: 2021-10-27
forum: Desktop Environments
---

### Post by indianajo on 2021-10-27
Just installed lubuntu20.04.3  10/26/21
Every 25 minutes a pop up window nags me that updated software is available and do I want it now or later?  I might want to update in 5 years. 
It takes 10 hours, 2 days, to backup files and prepare for an update. Plus assorted problems it took 2 days to resolve.   Is there anyway to stop this pop up window besides disconnecting the LAN cable from the modem? 
So far, I hate this update compared to lubuntu14.  But it will talk to the internet, which 14 found too insecure to communicate with after 10/07/21.  Everytime I copy & paste files from the DVD to hard drive, since there aren't 2 windows for the two I have to click down through the entire file structure to designate where the paste files are going.  Make a tedious process harder, why don't you. No, I don't want to buy a $30 64 gb usb flash drive that will corrupt the data after one use.  I've gotten about 1 or 2 uses out of the flash drives I've bought before they randomized the data.  Sunday 8 gb flash drive went to blanks after loaded with lubuntu18.04.  
Plus I cant put 30 images on the task bar with liximage. It stacks them up in its own box and only allows me to see one at a time. No I don't want a slide show, I don't want a **** timer dictating what I see.  I want to click the icon to pick a image as lubutu14 allowed me to do with multiple image viewers.  unbuntu 8.04 was even better, it allowed me to tile several images in one window.

---

### Post by GhX6GZMB on 2021-10-27
Considering your history of extremely dodgy .ISO sources and dodgy installs, I'm not taking this poat seriously until you tell us exactly what you've done. Be specific, ranting won't help.
I run Lubuntu 20.04 on four machines and have NEVER had this message.

Sorry.

---

### Post by guiverc on 2021-10-27
> **indianajo said:**
> Just installed lubuntu20.04.3  10/26/21
Every 25 minutes a pop up window nags me that updated software is available and do I want it now or later?  I might want to update in 5 years. 

The Update Notifier page can be found here - [https://manual.lubuntu.me/lts/4/4.4/Update-Notifier.html](https://manual.lubuntu.me/lts/4/4.4/Update-Notifier.html)

You can change the frequency of notifications via edit of 

`/usr/libexec/lubuntu-update-notifier/lubuntu-upg-notifier.sh`

change the `sleep 3600` (or 3,600 seconds) to an interval you're happy with (it was changed from 1 hour, or 3600 seconds to 24 hours or `sleep 86400` in [20.10/*groovy*]("https://launchpadlibrarian.net/480827201/lubuntu-update-notifier_0.1_0.2.diff.gz")).   I wrote more about this in an answer [here]("https://askubuntu.com/questions/1313885/how-can-i-change-the-frequency-of-the-lubuntu-update-notifier-lubuntu-20-04/1313987#1313987").

That was done for [subsequent releases]("https://launchpad.net/ubuntu/+source/lubuntu-update-notifier/+changelog") though it wasn't 25 minutes; so you maybe asking about the *release-upgrade* notification which isn't a Lubuntu specific tool; but details can be found in this manual page - [https://manual.lubuntu.me/lts/4/4.3/software_sources.html](https://manual.lubuntu.me/lts/4/4.3/software_sources.html)


Sorry I don't understand what you're asking after that, but if you're not happy with `lximage-qt` & prefer the options of other programs; install & use them. Myself I'm still partial to `gpicview` (a GTK+2 viewer used by LXDE; it's no longer *lightweight* on modern systems (*it no longer uses libs/toolkits already in RAM)*; but my fingers know it, & I have the RAM in my box to cope with the *extra **deprecated* libs co-existing in RAM.  We have choice; and can use whichever tools we prefer (*weighing their cost vs. benefit for us*)

---

### Post by indianajo on 2021-10-28
Okay, thanks gulverc.  Specific answers.  One nag per month might be tolerable. Computer has been doing the nagging even with the LAN cable removed.  I hope I can edit the update notifier parameter with leaf text editor or terminal.  
A program for viewing jpg's instead of the op system could be fine.  ubuntu software center disappeared from the control menu on this version, lub20.04.3. WIll have to reload lub14 on usb drive to look up the url.  
I abandoned Windows XP 20? years ago in part because of the constant updating when I wanted to use the computer.  It also would reboot every 30 minutes if it wasn't connected to the internet and registered.  **** microsoft, I didn't mind the $99 update biannually but nagging me constantly cost them $1000 or so over 20 years.   Obsoleting office97 with Win XP dll change was also a costly mistake. 
As far as ml9104 comment, somebody in this community needs to take control of lubuntu.org website. A splash to lubuntu.me would be fine.  I've been using ubuntu.org & for 15? years and lubuntu.org for 12? years or so, after finding about it from wikipedia. The extension wasn't on wikipedia, I made it up.  this is the first time I found most of the upload links on lubuntu.org->lubuntu.net were dead including all the links to amd64 versions.  The main upload link was obsolete, pointing to version 18 i386 was the only choice supported.  Whoever owns lubuntu.org and lubuntu.net is not malicious, just lazy or tired.

---

### Post by guiverc on 2021-10-28
lubuntu.org is a privately owned web site; that has nothing to do with Lubuntu.  The owner will not give up ownership, and there is nothing anyone can do to force ownership away from the owner; as it's their property (*even though they don't own the Lubuntu trademark*).

Many years ago the owner of lubuntu[.net] was involved with the Lubuntu project; which is why Lubuntu did post notices to it (*Lubuntu didn't have it's own web site at that time*), however when the owner of that site left the project; Lubuntu's access to it disappeared; the owner refused to give up, or sell the site to the Ubuntu project, as such all Ubuntu references to it were removed and a new website under Ubuntu control ([https://lubuntu.me/](https://lubuntu.me/)) was setup and used in its place. All other *flavors* that were using non-Ubuntu owned web sites were asked to ask to get the owners to give up ownership to make the sites Ubuntu owned (all other *flavor* owners gave up their sites & were thus thanked; in hopes this issue will not re-occur).

If you use certain browser extensions (esp. security related); going to lubuntu[.net] or lubuntu.[org] will warn you those sites are not legitmate (*not affiliated with the project*); but most browser by default do not do that.

Ubuntu[.org] is **also not a Ubuntu web site**.  [https://ubuntu.com/](https://ubuntu.com/) is the official site; having been so since 2004 when the project started.

---

### Post by indianajo on 2021-10-28
Okay, thanks. Legal problems to control lubuntu.org .  I inspected wikipedia today 10/28/21, url ubuntu.com doesn't appear on wikipedia ubuntu article.  Url lubuntu.me doesn't appear on wikipedia lubuntu article.  I'm supposed to find out official websites maybe from_ Linux Today_ magazine sold on newsstands in cities over 20 million population? No newstand here since 1996. Our university has closed stack library. no student id card, no info.  
Inspected ///computer/user/libexec/ file today with file manager.  No file lubuntu-update-notifier .  No file lubuntu-upg-notifier.sh 
Did a control-f search of root with file manager with invisible box checked. under computer/usr/lib it found lubuntu-update-notifier.py which I opened with featherpad.  there was a statement in there after the if then clauses that said "sleep 3600".  that sounds very likely to be the problem, 3600 seconds is 1 hour. I changed it to 400000 or about a month.  I was not allowed to save it. Permissions was owner read/write and the owner was root.  I am admin on this computer,   How do i get permission to save the new value?

---

### Post by guiverc on 2021-10-29
I don't know why you'd use wikipedia; given it's a general resource where almost anyone can edit it & add unofficial detail.   When I look at [https://en.wikipedia.org/wiki/Lubuntu](https://en.wikipedia.org/wiki/Lubuntu) though I see

> Official website  [lubuntu.me]("https://lubuntu.me/") [[IMG]https://upload.wikimedia.org/wikipedia/en/thumb/8/8a/OOjs_UI_icon_edit-ltr-progressive.svg/10px-OOjs_UI_icon_edit-ltr-progressive.svg.png[/IMG]]("https://www.wikidata.org/wiki/Q39238#P856")

but it's not where I'd go for information; without collaboration (*from a legitimate source that isn't related to the wiki editor that posted the detail on wikipedia*).

When the Ubuntu project was started; the original web site was [https://ubuntu.com/](https://ubuntu.com/) so that hasn't changed; and I'd trust esp. given details on a simple look up query (ie. `whois ubuntu.com`) show

```
Updated Date: 2020-04-27T09:04:47+0000
Creation Date: 2004-05-29T07:00:00+0000
```

Contrast that with your `ubuntu.org` and I know which I'd trust, and that is using nothing but a CLI terminal that I've had access to since my university dates, back in in the 1980s.

As for your permissions issue with Lubuntu; you'll generally need to elevate your privileges to write outside of your $HOME (/home/$USER directory); which is normally accomplished with `sudo`.

Myself I use the `vim` editor (*included with Lubuntu*), as `vi` was really useful in my college days given many terminals didn't have arrow keys and PCs (*cheaper clones accomplished when IBM BIOS was legally reverse engineered*) hadn't taken over back then and it beat line editors. I also try and avoid using GUI programs with elevated privileges (Lubuntu/LXQt currently won't stop you, but it's stopped already in some environments for security reasons).

---

### Post by yancek on 2021-10-29
>  I might want to update in 5 years.  

Security updates for any OS need to be done a lot more frequrently than every 5 years.  This is how users who won't keep their computer up to date jeopardize others.
I see this nagging message about once a week and as explained, you can change that to what you want.  I don't know what you are doing that takes "10 hours, 2 days".  The update rarely takes more than 30 minutes if done on a regular basis.  

In post 3, it is explained how to modify this notification, it's a simple text file with the leafpad text editor.  An internet connection has nothing to do with how you get the notification. 

You then move on to Lubuntu 14 being to insecure on the internet, well it hasn't been supported or update for  years so of course that's the case.  You then move to copying files from a DVD to a hard drive.  You might have better luck resolving problems if you stuck to one problem at a time.  This thread has wandered off topi like a 3 legged dog on steroids.

---

### Post by indianajo on 2021-10-29
> **guiverc said:**
> 
As for your permissions issue with Lubuntu; you'll generally need to elevate your privileges to write outside of your $HOME (/home/$USER directory); which is normally accomplished with `sudo`.
Myself I use the `vim` editor (*included with Lubuntu*), as `vi` was really useful in my college days given many terminals didn't have arrow keys and PCs (*cheaper clones accomplished when IBM BIOS was legally reverse engineered*) hadn't taken over back then and it beat line editors. I also try and avoid using GUI programs with elevated privileges (Lubuntu/LXQt currently won't stop you, but it's stopped already in some environments for security reasons).
Getting to the point.  Read about bash today for 2 hours,  very perplexed.  Did get qterminal to recognize sudo dm, which I didn't execute because it is scary and not on any list.  Featherpad for unexperienced coders like me would show me the permissions for usr/lib/lubuntu-update-notifier/lubuntu-notifier.py file but wouldn't let me change the permissions to anybody read-write . Or at least my username read-write (nobody else touches this computer).
Can you give me a string to type into qterminal to update permissions for usr/lib/lubuntu-update-notifier.py ?
learning to use vim editor is a bit of a stretch.   Did read wikipedia "list of unix commands" no help. Wikipedia "list of gnu utilities" had a command chmod which changes file permissions had a lot of scary detail.  A display permissions cf a file command would be useful to use first, but haven't found one yet.  Thanks for looking.

---

### Post by guiverc on 2021-10-29
> **indianajo said:**
> Did get qterminal to recognize sudo dm, which I didn't execute because it is scary and not on any list.

I don't know what you mean here, I have no command `dm`, and the DM (*display manager*) used by Lubuntu since 18.10 is `sddm`.

> **indianajo said:**
> Featherpad for  unexperienced coders like me would show me the permissions for  usr/lib/lubuntu-update-notifier/lubuntu-notifier.py file but wouldn't  let me change the permissions to anybody read-write . Or at least my  username read-write (nobody else touches this computer).
Can you give me a string to type into qterminal to update permissions for usr/lib/lubuntu-update-notifier.py ?
learning to use vim editor is a bit of a stretch.   Did read wikipedia  "list of unix commands" no help. Wikipedia "list of gnu utilities" had a  command chmod which changes file permissions had a lot of scary detail.   A display permissions cf a file command would be useful to use first,  but haven't found one yet.  Thanks for looking.

A 

```
sudo featherpad /usr/libexec/lubuntu-update-notifier/lubuntu-upg-notifier.sh
```

 for me opens the file up in `featherpad` with the warning that it's a root instance. Your last post however used a different filename (*path specifically*) to my prior post.

Featherpad is a text editor; I'd use a command like `chmod` to change file attributes/stats; as text editors are designed to change contents of files; not the file metadata (*file mode bits*).

Looking at the file on my system (which is *heavily modified* and running *jammy *not *focal*)

```
guiverc@d960-ubu2:~$   stat /usr/libexec/lubuntu-update-notifier/lubuntu-upg-notifier.sh
  File: /usr/libexec/lubuntu-update-notifier/lubuntu-upg-notifier.sh
  Size: 1217            Blocks: 8          IO Block: 4096   regular file
Device: 801h/2049d      Inode: 524518      Links: 1
Access: (0755/-rwxr-xr-x)  Uid: (    0/    root)   Gid: (    0/    root)
Access: 2021-10-30 13:52:22.223764581 +1100
Modify: 2021-02-15 11:06:03.000000000 +1100
Change: 2021-02-16 09:46:40.386531491 +1100
 Birth: 2021-02-16 09:46:40.046534105 +1100
```

It shows that the **owner** (root) has RWX (read write & execute or 7) permissions, those in the **group** have RX (read & execute or 5) & everyone else has RX (read & execute permissions or 5).

Me, I'd personally likely use

```
sudo chmod a+w /usr/libexec/lubuntu-update-notifier/lubuntu-upg-notifier.sh
```

ie. give **ALL** **write** permissions; but I'd prefer to test the command before suggesting it. I see no consequences on my current box; but don't have a *focal* box *up* (*turned on*) nor time to test for any side effects of the command currently.


> **indianajo said:**
> learning to use vim editor is a bit of a stretch.

Smart move I suspect. It's fast, efficient & a great editor, but I doubt I'd be using it if I didn't need to use it long long ago when dumb terminals didn't have arrow keys. The real benefit is knowing is not the editor; but so many POSIX/UNIX functions use the same syntax as found in `vi`; so when viewing a `man` (manual or help page); I can just search/find things using commands I'd use in `vi`(as example; ie. it uses a very common *shorthand* found throughout much of GNU/Linux, Unix, BSD, OSX etc OS when at command level)

---

### Post by Paddy Landau on 2021-10-31
> **guiverc said:**
> lubuntu[dot]org is a privately owned web site … lubuntu[.dot]net was involved with the Lubuntu project … new website under Ubuntu control ([https://lubuntu.me/](https://lubuntu.me/))
This is all correct. Unfortunately, the way that the internet is set up, it's not possible to get control of renegade people unless they break the law (even then, not always possible).

The top result in an internet search results in the wrong Lubuntu site, leading people like you to (unwittingly) download dodgy software. It's not your fault, but unfortunately you have been landed with it.

If you have downloaded from an invalid Ubuntu website or from lubuntu[dot]net, *assume that the software is compromised*. Do **not** trust it!

In your position, I would download the correct, valid software from the [official Lubuntu website]("https://lubuntu.me/"), and overwrite your existing installation from scratch. I recommend the latest LTS version, which is 20.04 (the next LTS version will be 22.04).

I know that you don't what to hear this, but we aren't going to give you false information. It's for your own safety.

Also, regarding updates, you should *never* delay security updates. Waiting five years, even for non-security updates, is a guarantee that you'll have problems! It's also a good idea to run all the other updates when prompted.

If you open Software & Updates > Updates, you can tailor your reminders. I strongly recommend that you automatically check for updates daily, and set security updates to download and install automatically. A recent example of why that is important was a dangerous bug in Chrome, which was fixed (IIRC) overnight.

---

### Post by TheFu on 2021-10-31
guiverc, I've been telling folks to use **sudoedit** to edit system files for about 4 yrs.  Running most GUI programs with sudo when we aren't sure exactly which OS release they have can be dangerous - in some releases the HOME doesn't get reset under sudo, which means directory and config files can be owned as root in the user's HOME.  I know that about 5 yrs ago, someone in my LUG did a fresh install, then used *sudo gedit /etc/hosts* ... as one of their first commands.  They were never able to log into that system again, because the ~/.config/ directory was owned by root with 700 permissions. Basically, nothing gnome-based worked.  Login loop resulted.

To the OP, learning to edit system files, safely, is a basic skill required for people managing their own multi-user computer.  All Linux systems are multi-user.  The basic skills are best learned in order to avoid huge gaps and misunderstandings.  [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) is a good source of this basic information and skills that isn't tied to any GUI.  As you know, the GUI changes with each release, but the underlying OS doesn't change *that much* between releases. Anyway, that no-hassle book has all the basic skills and understanding to handle a multi-user system.

Newer releases of desktop Ubuntu/Lubuntu OSes have changed the package manager name, but you can always use apt-get, if you prefer. Or you can install the old tools like synaptic, if you prefer that. You have the choice.

If you connect the system to the internet, then it needs to be patched.  If you don't connect it to the internet, then the only reason to patch is to protect against other bad systems on your local network OR to get new software installed.

I prefer to disable all nags about updates and to manually patch my many systems weekly. I have a script that does this, so I only need to enter 1 command from 1 system and it connects to every other system and runs the update and full-upgrade APT commands for me. This happens in a window and gets logged, so if anything bad happens, I can see the log for the issues.  

The more we know, the more we can have the computer(s) work for us.

---

### Post by indianajo on 2021-10-31
Thanks Guiverc for post #10.  
In time since last post,  read a lot on en.wikipedia, decided terminal (which allows sudo chmod to run) understands posix instead of unix.  Terminal runs bash but that is all about program flow and nothing about editing instructions I gather after hours wasted reading about it.  Bing found me a tutorial about posix, [http://web.cs.ucla.edu/~miryung/teaching/EE461L-Spring2012/labs/posix.html#:~:text=Directories%20%20%20%2F%20%20%20%22root%22%20directory](http://web.cs.ucla.edu/~miryung/teaching/EE461L-Spring2012/labs/posix.html#:~:text=Directories%20%20%20%2F%20%20%20%22root%22%20directory) which was useful.  Couldn't find a ls command parameter that allowed viewing privileges of lubuntu-upg-notifier.sh under terminal but could look at the privileges with file manager. Privlleges were 111 for root, 101 for group & everyone.  Used terminal chmod to change privileges of lubuntu-upg-notifier.sh to 777 . Use feather text editor to change sleep time of update notification from 3600 to 100000 or 26 hours. Used terminal to  change privileges of lubuntu-upg-notifier.sh back to 755 . Boot.  Problem solved. Popup box notifies me to update lubuntu right after sign-on, then not again for 26.6 hours. Thanks everybody.

---

### Post by guiverc on 2021-10-31
> **TheFu said:**
> guiverc, I've been telling folks to use **sudoedit** to edit system files for about 4 yrs.  Running most GUI programs with sudo when we aren't sure exactly which OS release they have can be dangerous - in some releases the HOME doesn't get reset under sudo, which means directory and config files can be owned as root in the user's HOME. 


**Thanks** @TheFu

I wish I'd thought of `sudoedit`; alas I didn't.  I said what I'd do; as it was truthful, and my *bad habits* showed through. 

Thank you for the correction/advice, and sorry @indianajo  (*I wish it'd occurred to me to suggest `sudoedit` but it didn't*)

> **indianajo said:**
> ... In time since last post,  read a lot on en.wikipedia, decided terminal  (which allows sudo chmod to run) understands posix instead of unix.
... Couldn't find a ls command parameter that allowed  viewing privileges of lubuntu-upg-notifier.sh under terminal but could  look at the privileges with file manager. 


I'm not sure what you're looking for, `ls -lah` I commonly use; although if it's only a single file I'd likely use `stat.

Well done on the learning !!!  :P  We're all still learning; my issue is forgetting much of what I did learn, and my old habits returning... (eg.  `sudoedit` :o )

---


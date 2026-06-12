---
title: "Brand new user, Firefox will not open"
date: 2009-05-30
forum: General Help
---

### Post by mnttnlyzr on 2009-05-30
Dual boot Vista/Ubuntu 9.04

Tried getting ubuntu-restricted-extras to watch a DVD. Next thing I knew (may be unrelated), Firefox opens two tabs but only one window, the second tab doesn't respond to input and closes after 10s or so, and the open window only does hyperlinks and previous searches, no back button, no new searches, etc.

Ran terminal command mv~/.mozilla ~/.mozilla.backup which got rid of the opening window and left the worthless tab that closes automatically and won't respond to input.

Now I have to boot to Vista to just access internet (where the answers are) and I can't stand having this OS after only three hours of use.

Please someone restore my optimism in Ubuntu.

---

### Post by Sef on 2009-05-30
Applications > Accessories > Terminal

type in firefox; post any error messages that you get in here.

---

### Post by mnttnlyzr on 2009-05-30
Thank you for replying.

I followed your instructions. No messages appear. It looks like this:

mnttnlyzr@mnttnlyzr-desktop:~$ firefox

I press enter, it pauses, then repeats originally query, so in total it says:

mnttnlyzr@mnttnlyzr-desktop:~$ firefox
mnttnlyzr@mnttnlyzr-desktop:~$

I wanted to be sure you know that it was working fine for a while, but at some point it stopped. It could have been when I was trying to get DVD's to play, I don't know.

I think I should've also mentioned originally that I am on a 32-bit system.

Also, I've uninstalled/reinstalled but no improvement happened.

---

### Post by Yellow Pasque on 2009-05-30
See if firefox safe mode works:
```
firefox -safe-mode
```

---

### Post by mnttnlyzr on 2009-05-30
Nothing happened, just like before.

Looked like this by the time I was done:

mnttnlyzr@mnttnlyzr-desktop:~$ firefox -safe-mode
mnttnlyzr@mnttnlyzr-desktop:~$ firefox -safe -mode
mnttnlyzr@mnttnlyzr-desktop:~$ firefox

And so on; it would only return to the originally query. No windows opened or anything. I would wait a few seconds after each entry because I'm so new I don't know what to expect, but nothing would happen.

---

### Post by ActiveFrost on 2009-05-30
Open System Monitor and check if it's not already running ( it will not let me to open a new Firefox window if at least 1 "crashed" Firefox service already exists ) and Kill it ( if any ).

---

### Post by mnttnlyzr on 2009-05-30
Looking in system monitor, there isn't any "firefox" in the processes list.

Clicking on the Firefox icon doesn't change the list, and typing "firefox" into the terminal doesn't either.

---

### Post by trench.me on 2009-05-30
```
sudo dpkg --configure -a
```

or

```
sudo apt-get -f install
```

---

### Post by trench.me on 2009-05-30
Sorry, that was written quickly and without explanation.

One of the above two should fix whatever broke after you installed the extras. 

Why did you move your Moz dir? If you move it back to its original location and do one of the two listed options above, you should be good to go.

EDIT: Possibly what you meant to do was **cp** the .mozilla/ dir, not **mv**

---

### Post by mnttnlyzr on 2009-05-30
I honestly don't know what I did or why. I was poking around on the forums and found a problem I though was the same so I tried what worked there. I probably added another problem onto the original.

When you say to move the Moz dir back to its original location, I don't know how to do that, but I'd like to learn.

I typed the two commands you gave me and it didn't seem to change anything, but then I haven't moved the Moz dir.

I'm the newest beginner ever, I think. I had just installed Ubuntu for the first time when Firefox got soaked. It worked for maybe half-an-hour. I don't know how to use the terminal, I was hoping to learn as I went. I didn't expect this out of the box, so to speak, so I really need some elementary-type help.

Here are the results of the commands:

mnttnlyzr@mnttnlyzr-desktop:~$ sudo dpkg --configure -a
[sudo] password for mnttnlyzr:

I typed in my user password and pressed enter. Returned to:

mnttnlyzr@mnttnlyzr-desktop:~$

and did not appear to change anything. Firefox is still acting badly.

Next:

mnttnlyzr@mnttnlyzr-desktop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
mnttnlyzr@mnttnlyzr-desktop:~$

Firefox still inop.

I thought you may need this information.

---

### Post by drs305 on 2009-05-30
> **mnttnlyzr said:**
> I honestly don't know what I did or why. I was poking around on the forums and found a problem I though was the same so I tried what worked there. I probably added another problem onto the original.

When you say to move the Moz dir back to its original location, I don't know how to do that, but I'd like to learn.

I typed the two commands you gave me and it didn't seem to change anything, but then I haven't moved the Moz dir.

This is probably why you tried moving the .mozilla folder: 
Moving (renaming) $HOME/.mozilla would have made the user's configuration files unavailable to Firefox. When firefox started and didn't find .mozilla/firefox, it would have created a new firefox configuration file for the user. If the problem had been in the user's original configuration files, this probably would have solved the problem.

Another way to accomplish almost the same thing would have been to start firefox with a new user (and new configuration file). This would be done with the command "firefox -p" and then creating a new profile.

---

### Post by trench.me on 2009-05-30
> **drs305 said:**
> 
Moving (renaming) $HOME/.mozilla would have made the user's configuration files unavailable to Firefox. 

Good call. 

Okay, **mnttnlyzr**, you should know that by creating a new Firefox profile (the 'firefox -p' method explained above) literally creates a fresh (read: *different*) profile for Firefox. None of the original data remains associated with the new profile (like stored passwords and addons), though it could easily be restored from the backup you created. If you have no qualms with losing this data, or don't have much stored to begin with, then let's try another route.

**WARNING: ONLY DO THIS IF YOU'VE NO DATA YOU NEED RETAINED IN FIREFOX.**

Reinstall firefox:

```
sudo apt-get remove --purge --auto-remove firefox -y
rm -R ~/.mozilla/ && rm -R ~/.mozilla.backup/
sudo apt-get update && sudo apt-get install firefox -y
```

---

### Post by mnttnlyzr on 2009-05-30
Typing in the code gave me this message:

E: command line option 'R' [from -R] is not known

BTW do I type that all in at once, or do I break it into two parts, each beginning with "sudo"?

---

### Post by K.L. on 2009-05-30
> **mnttnlyzr said:**
> Typing in the code gave me this message:

E: command line option 'R' [from -R] is not known

BTW do I type that all in at once, or do I break it into two parts, each beginning with "sudo"?


Actually, there are three parts.

I think you should use this:

```
rm -rf ~/.mozilla/ && rm -rf ~/.mozilla.backup/

```Instead of this:
```
rm -R ~/.mozilla/ && rm -R ~/.mozilla.backup/

```

---

### Post by trench.me on 2009-05-30
Whenever you see "code" written like that, each line represents a new line unless stated otherwise.

**1. Paste the following into a terminal:**
```
 sudo apt-get remove --purge --auto-remove firefox -y
``` The above will remove firefox, and any residual firefox entities. You'd normally be prompted with a few "are you sure?" statements but the '-y' at the end of the line tells the system to assume yes is the answer to anything it's going to ask you.

**2. Upon return to prompt, paste the following: **
```
 rm -R ~/.mozilla/ && rm -R ~/.mozilla.backup/
```'rm' is remove, '-R' is recursive (meaning it will take all directories and files within that directory... **recurssive removal of any directory has to be done with extreme care and is typically not recommended unless you are confident in what you are doing**. The '&&' says "and then do this:" which is the recursive removal of the second directory you earlier created.

**3. Upon return to prompt, paste the following line:**
```
 sudo apt-get update && sudo apt-get install firefox -y
```'update' is as it sounds - it updates apt-get. And then apt-get installs Firefox.
Again, yes is assumed on all questions.

---

### Post by mnttnlyzr on 2009-05-30
Hold on, retrying.

---

### Post by trench.me on 2009-05-30
> **K.L. said:**
> Actually, there are three parts.

I think you should use this:

```
rm -rf ~/.mozilla/ && rm -rf ~/.mozilla.backup/

```Instead of this:
```
rm -R ~/.mozilla/ && rm -R ~/.mozilla.backup/

```

-rf is extremely dangerous. I'd never recommend an -rf to anyone that is clearly this new to command line operations.

---

### Post by mnttnlyzr on 2009-05-30
Well, I tried both ways, -rf and -R.

-rf didn't seem to do anything, and there was no improvement after finishing the sequence.

-R gave me the message: rm: cannot remove '/home/mnttnlyzr/.mozilla/': No such file or directory.

Maybe the -rf already got it?

After it gave me that message, I didn't do the install (3rd line).

BTW if it's not apparent, I'm going back and forth from Vista to Ubuntu to post here and type in commands there, copying by hand. So there's some delay for me to find out if it works or not.

---

### Post by penguin-of-doom on 2009-05-30
well, are you logged in as root? Some packages does not work when you are logged in as root. When you are logged in as root, log in as normal user and try then.

mfg

---

### Post by trench.me on 2009-05-30
The /home/mnttnlyzr/.mozilla/ (AKA ~/.mozilla) directory didn't exist because you moved it earlier. I should have warned you about that. 

Okay, everything is exactly as it should be. It's perfectly safe to run the third line and install firefox again.

EDIT: Also, the reason it "didn't seem to do anything" is because when you rm a file or directory it instantly removes it - you'll typically see no extra action in the terminal, it just returns you to a prompt.

---

### Post by mnttnlyzr on 2009-05-30
I did the install, it seemed to work fine in terminal, but there's no change when trying to open the program.

It strikes me as strange that the icon for Firefox at the top bar doesn't go away when I uninstall the program, but maybe it's normal?

Anyway, it's still refusing to come out and play.

Thank you so much for walking me through this.

EDIT: Penguin-of-doom: Each time it boots I enter a user name and password. Is it possible to still be logged in as root in this case?

Re-EDIT: But now that I think about it, it worked fine to begin with and I haven't changed any login qualities so it's doubtful this is it. Also my command prompt ends in "$". Thank you, though.

---

### Post by trench.me on 2009-05-30
Typing sudo let's you perform root actions. You don't need to be root to remove your own user-directories and user-files (which is what ~/.mozilla is), ergo you didn't need to be root to perform that action.

Hm. I'm still chewing on this. It could be that backup directory didn't get removed because the command hung on the non-existing ~/.mozilla. 

Try this. Paste the following in a terminal.
```
ls -a | grep moz
```The output should only be the following (unless you've created other moz things.)
```
.mozilla
```If it lists anything else, especially that backup directory created earlier,  repeat all three of the steps to reinstall firefox. (It will no longer get hung on the missing directory because you just created the directory when you reinstalled it.)

After doing this run the package fixes I first posted again to make sure no packages are broken.

```
sudo dpkg --configure -a
```and

```
sudo apt-get -f install
```Then, do not click any firefox icons.

From the terminal type:

```
firefox
```If the terminal throws some errors/anything at you instead of, or while, firefox smoothly opens - write down everything the terminal says and return here with that. If nothing at all happens, then I'm a bit stumped. But either way, return with any/all results. I'm very curious to see what's happened here.

(And no need for thanks, this is what the Ubuntu community is here for. :D )

---

### Post by mnttnlyzr on 2009-05-30
I didn't make it very far. The first code input, namely 'ls -a | grep moz' didn't yield any outputs.

EDIT: I went back after posting first paragraph and same results. Also finished complete instructions (sudo dpkg...) but no change.

---

### Post by trench.me on 2009-05-30
Didn't mean to leave you hanging but I wanted to put some time between that last reply and this one in hopes that some new passersby might read this when I bump it, because at this time I'm afraid I'm out of recommendations. 

Don't give up though. I have a feeling this revolves around some misinterpreted command-line attempts before you started this thread and I'm pretty sure you'll get the help you need.

In the meantime if you could post any more information on what you may have done prior to starting this thread that would be quite helpful.

One way to find out what you did prior to starting the thread is bash history. 

Open a terminal and hit the UP arrow-key. This will scroll through the many lines you've entered throughout all of this, and hopefully back to the initial commands surrounding the 

```
mv ~/.mozilla ~./mozilla.backup
```

Anything you did around that point would definitely be worth posting for us here.

Another worthwhile thing would be to look at your System > Administration > Log File Viewer. Poke around in it for any errors, especially if they relate to Mozilla or Firefox. 

Hopefully someone else might have some helpful advice.

---

### Post by mnttnlyzr on 2009-05-30
I decided to make a clean start, so I booted from CD, used partition manager to delete the Ubuntu partitions, and then reinstalled onto the newly created free space. I didn't know what else to do.

This second time around I'll be more careful about getting DVD's to play, and I'll definitely try to get live answers before trying to fix a problem and risk making it worse. I went in a little overconfident last time and realize now that I am definitely in a state of ignorance.

It seems it's okay now.

---

### Post by -kg- on 2009-05-30
I found the way to get DVDs to play.  Go to the [Medibuntu page]("https://help.ubuntu.com/community/Medibuntu") and follow the instructions there.  You will want to at the least install libdvdcss2 (around halfway down the page under "Playing Encrypted DVDs," and personally I installed the restricted codecs.  That worked for getting my DVD players up to playing DVDs.

---


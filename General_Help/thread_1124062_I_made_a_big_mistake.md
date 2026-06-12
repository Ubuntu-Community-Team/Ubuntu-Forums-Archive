---
title: "I made a big mistake"
date: 2009-04-13
forum: General Help
---

### Post by chaeussinger on 2009-04-13
I was practicing command line stuff when I accidentally moved the BIN folder to my desktop. I tried to get it back to it's original location, but I was getting authority issues from root. I tried to login as root, but Ubuntu prevented me from doing so. I tried using SUDO in the terminal, but even that didn't do what I wanted it to.

To the best of my knowledge, I did everything I could. To my mistake, I reset my system, hoping that the BIN, although sounding important, was not a folder needed for booting up. Because of that, I'm back to Vista. I tried things like installing the Ext2 Windows driver from fs-driver.org, but that didn't help, as the file system for Ubuntu is Ext3.

So unless someone can suggest a different driver, I'm giving up on that.

So here's the problem: I can't boot Ubuntu because I accidentally misplaced an important folder through the terminal (under SUDO), I'm using Windows, and the safest thing I can think of is somehow accessing my Ubuntu partition from Windows and move my BIN folder from Ubuntu's desktop to the directory it should be located. But that's proving to be challenge. Is there software available to restore the system, as with Windows Recovery Disks?

If not, what can I do?

---

### Post by 3rdalbum on 2009-04-13
Have you tried booting up an Ubuntu live CD, mounting your hard disk and moving /bin back to its correct location?

Even if moving it back fails, you can use the CD to back up your /home directory, because the entire Gnu/Linux system hinges upon /bin.

---

### Post by fdrake on 2009-04-13
> **chaeussinger said:**
> I was practicing command line stuff when I accidentally moved the BIN folder to my desktop. I tried to get it back to it's original location, but I was getting authority issues from root. I tried to login as root, but Ubuntu prevented me from doing so. I tried using SUDO in the terminal, but even that didn't do what I wanted it to.

To the best of my knowledge, I did everything I could. To my mistake, I reset my system, hoping that the BIN, although sounding important, was not a folder needed for booting up. Because of that, I'm back to Vista. I tried things like installing the Ext2 Windows driver from fs-driver.org, but that didn't help, as the file system for Ubuntu is Ext3.

So unless someone can suggest a different driver, I'm giving up on that.

So here's the problem: I can't boot Ubuntu because I accidentally misplaced an important folder through the terminal (under SUDO), I'm using Windows, and the safest thing I can think of is somehow accessing my Ubuntu partition from Windows and move my BIN folder from Ubuntu's desktop to the directory it should be located. But that's proving to be challenge. Is there software available to restore the system, as with Windows Recovery Disks?

If not, what can I do?

1.rebbot the computer.
2.select ubuntu recovery mod vers....(wathever version u have)
3.select log in root
4.after u login type:
    cp -R /home/your_user_name_here/Desktop/bin /bin
6.pray (hope u didn't change anything in the bin folder before)
5.reboot and good luck

---

### Post by hyper_ch on 2009-04-13
It is advised to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

See the forums policy, especially section II.2: [http://ubuntuforums.org/index.php?page=policy](http://ubuntuforums.org/index.php?page=policy)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

### Post by CatKiller on 2009-04-13
> **3rdalbum said:**
> Have you tried booting up an Ubuntu live CD, mounting your hard disk and moving /bin back to its correct location?

Even if moving it back fails, you can use the CD to back up your /home directory, because the entire Gnu/Linux system hinges upon /bin.

++

You can get a file browser window with root permissions with ```
gksudo nautilus
```

---

### Post by 3rdalbum on 2009-04-13
> **fdrake said:**
> 1.rebbot the computer.
2.select ubuntu recovery mod vers....(wathever version u have)
3.select log in root
4.after u login type:
    cp -R /home/your_user_name_here/Desktop/bin /bin
6.pray (hope u didn't change anything in the bin folder before)
5.reboot and good luck

It won't work. "cp" is inside /bin... or to be more precise, on this user's system it is now in /~Desktop/bin. The Dash shell which the system uses to run the init scripts, is also inside /~Desktop/bin, so the system wouldn't even come up. That's why I suggested a live CD.

---

### Post by mb_webguy on 2009-04-13
Couldn't he just use the command "sudo /home/*username*/Desktop/bin/cp /home/*username*/Desktop/bin /bin"?

---

### Post by chaeussinger on 2009-04-15
> **3rdalbum said:**
> Have you tried booting up an Ubuntu live CD, mounting your hard disk and moving /bin back to its correct location?

Yeah, but I got permission errors.

> 
Even if moving it back fails, you can use the CD to back up your /home directory, because the entire Gnu/Linux system hinges upon /bin.
Really? How do I do that?

---

### Post by chaeussinger on 2009-04-15
> **mb_webguy said:**
> Couldn't he just use the command "sudo /home/*username*/Desktop/bin/cp /home/*username*/Desktop/bin /bin"?
:O

You can put commands in directory names? That makes moving folders much easier. Thanks for pointing out that possibility, I'll try it through the Live CD.



Edit: Oops, I didn't mean to double post. Is there a way this post could be merged with my last one?

---

### Post by tobydeemer on 2009-04-15
I think the quickest way to do this would be boot a live CD as suggested >> 

then when you're using the Live CD desktop, hit Alt+F2 to get a run box >>

type in gksu nautilus, hit enter >>

hit Ctrl+T so you have a root-powered Nautilus window with two tabs >> 

In one tab, navigate to the dir on your hard drive /home/username/Desktop 
        >> should see your bin folder there

In the second tab, navigate to / on your hard drive.

Drag the bin folder from the first tab over to the second tab.

This way, you don't have to worry about whether the system will boot properly or be able to run commands w/ permissions, etc.

Let us know how it goes...
Hope that helps.

---

### Post by damis648 on 2009-04-15
> **mb_webguy said:**
> Couldn't he just use the command "sudo /home/*username*/Desktop/bin/cp /home/*username*/Desktop/bin /bin"?

Bash is also in /bin. :popcorn:

---

### Post by chaeussinger on 2009-04-16
It worked! I did what tobydeemer suggested. But to avoid such mishaps in the terminal again, could someone try to remind me what I did? The terminal was acting weird when I attempted to copy that folder to my desktop.

---

### Post by damis648 on 2009-04-16
/bin is the directory that keeps all the system's executables, like cp, mv, bash, ls, etc. all of those. When you moved it, your system obviously would stop working.

---

### Post by tobydeemer on 2009-04-16
> **damis648 said:**
> /bin is the directory that keeps all the system's executables, like cp, mv, bash, ls, etc. all of those. When you moved it, your system obviously would stop working.

Exactly- to parallel Windows, it'd be like moving your C:\program files directory to another location, and then Windows wouldn't know where to look for program executables.

Glad to hear that it worked out though. 

(And don't let this dissuade you from the terminal. Great learning experience, right?)

Cheers.

-TD.

---

### Post by chaeussinger on 2009-04-16
> **tobydeemer said:**
> Exactly- to parallel Windows, it'd be like moving your C:\program files directory to another location, and then Windows wouldn't know where to look for program executables.

Glad to hear that it worked out though. 

(And don't let this dissuade you from the terminal. Great learning experience, right?)

Cheers.

-TD.
Yeah, it was. But when I tried copying it, it gave me weird errors regarding syntax and whatnot. Moving it (from the terminal) is a different story. Can anyone help me pinpoint what I might have done to prevent this from happening again? To me, it's still a random error (lesson learned: never move system folders from the command line).

---

### Post by tobydeemer on 2009-04-16
Was it maybe part of something else you were trying to do? Install another app?

anthing like this

```
 mv / /home 
```

or ```
 mv /bin /home/user/Desktop/ 
```

would spell bad news (the second ex. being something like what you saw.)

---

### Post by chaeussinger on 2009-04-16
> **tobydeemer said:**
> Was it maybe part of something else you were trying to do? Install another app?

anthing like this

```
 mv / /home 
```

or ```
 mv /bin /home/user/Desktop/ 
```

would spell bad news (the second ex. being something like what you saw.)
I was using SUDO and the second command. I was under the assumption that the terminal wouldn't reject the BIN folder returning to its original location through SUDO. Apparently I was wrong, or that the terminal was acting weird.

But all of this was for educational purposes. Clearly there's something with greater permissions than SUDO that determines what files are allowed to go into the main directory.

---

### Post by CatKiller on 2009-04-16
> **chaeussinger said:**
> Clearly there's something with greater permissions than SUDO that determines what files are allowed to go into the main directory.

Convention.

sudo is just a program, the same as cp, mv, or any number of programs on your computer. The place where programs are kept is stored in the $PATH setting. Anything that's in your $PATH can be invoked just with its name, so you don't have to type /usr/bin/sudo /bin/cp... whatever. You'd moved most of the important programs out of your $PATH and into some other location, which is why they didn't work just by typing their name.

It's not like some higher power was mysteriously stopping you from doing what you wanted, it was that you'd taken all the tools that would let you do what you wanted and locked them in a box. In a disused lavatory. In the basement. With a sign on that said, "beware of the leopard."

---

### Post by chaeussinger on 2009-04-16
> **CatKiller said:**
> Convention.

sudo is just a program, the same as cp, mv, or any number of programs on your computer. The place where programs are kept is stored in the $PATH setting. Anything that's in your $PATH can be invoked just with its name, so you don't have to type /usr/bin/sudo /bin/cp... whatever. You'd moved most of the important programs out of your $PATH and into some other location, which is why they didn't work just by typing their name.

It's not like some higher power was mysteriously stopping you from doing what you wanted, it was that you'd taken all the tools that would let you do what you wanted and locked them in a box. In a disused lavatory. In the basement. With a sign on that said, "beware of the leopard."
What I meant by that is something like Root. You can't login as Root in Ubuntu, can you? I, a briefly-former openSUSE user, know that I can login as Root in Ubuntu.

BTW is $PATH another way of referring to the / directory?

---

### Post by CatKiller on 2009-04-16
> **chaeussinger said:**
> What I meant by that is something like Root. You can't login as Root in Ubuntu, can you? I, a briefly-former openSUSE user, know that I can login as Root in Ubuntu.

No. Root and sudo are largely synonymous. Root is the super-user, able to do anything on the computer. Sudo is a utility that will temporarily allow a suitably-authorised user to become root for the duration of a command.

[This page]("https://help.ubuntu.com/community/RootSudo") will give you more information, if you're interested.

Logging in as root would mean that you (or someone pretending to be you) could do absolutely anything to your computer without any warning that it was a bad plan. This would be problematic for inexperienced users, which is why Ubuntu doesn't let you log in as root. The fact that you need to enter your password again is supposed to serve as a reminder that what you're doing requires special care. But running a command as root the old-fashioned way, and running a command as root using sudo are exactly the same in their effect.

Remember, it's not because of permissions that you couldn't move files around. It's because you broke the tool that moves files around.

> 
BTW is $PATH another way of referring to the / directory?No. $PATH is a system variable that lists the locations that the computer should expect to find programs, so that when you type a command it only has to look at a short list of files to determine what to do next, rather than having to trawl through your entire hard drive for every part of every command that you might choose to give. You can see what your $PATH variable is currently set to with ```
echo $PATH
```/ is something entirely different. / is the part of your filesystem tree to which all other accessible directories are ultimately attached. Think of it kind of like the C: drive in DOS, except if all other drives and computers and running processes and random number generators and... were expressed as some file in a directory on your C: drive.

I think you probably need to read a bit more before you run any other commands that start sudo...

---

### Post by meho_r on 2009-04-16
> **chaeussinger said:**
> Yeah, it was. But when I tried copying it, it gave me weird errors regarding syntax and whatnot. Moving it (from the terminal) is a different story. Can anyone help me pinpoint what I might have done to prevent this from happening again? To me, it's still a random error (lesson learned: never move system folders from the command line).

A little advice: install VirtualBox and install Ubuntu inside it. Then practice all commands you like :) If you break something, it's not a big deal, only 15 mins to reinstall.

---

### Post by chaeussinger on 2009-04-16
> **CatKiller said:**
> No. Root and sudo are largely synonymous. Root is the super-user, able to do anything on the computer. Sudo is a utility that will temporarily allow a suitably-authorised user to become root for the duration of a command.

[This page]("https://help.ubuntu.com/community/RootSudo") will give you more information, if you're interested.

Logging in as root would mean that you (or someone pretending to be you) could do absolutely anything to your computer without any warning that it was a bad plan. This would be problematic for inexperienced users, which is why Ubuntu doesn't let you log in as root. The fact that you need to enter your password again is supposed to serve as a reminder that what you're doing requires special care. But running a command as root the old-fashioned way, and running a command as root using sudo are exactly the same in their effect.

Remember, it's not because of permissions that you couldn't move files around. It's because you broke the tool that moves files around.

No. $PATH is a system variable that lists the locations that the computer should expect to find programs, so that when you type a command it only has to look at a short list of files to determine what to do next, rather than having to trawl through your entire hard drive for every part of every command that you might choose to give. You can see what your $PATH variable is currently set to with ```
echo $PATH
```/ is something entirely different. / is the part of your filesystem tree to which all other accessible directories are ultimately attached. Think of it kind of like the C: drive in DOS, except that all other drives and computers and running processes and random number generators were expressed as some file in a directory on your C: drive.

I think you probably need to read a bit more before you run any other commands that start sudo...
Will do. Thanks for explanation and advice.

> **meho_r said:**
> A little advice: install VirtualBox and install Ubuntu inside it. Then practice all commands you like :) If you break something, it's not a big deal, only 15 mins to reinstall.
Thanks, I'll do that.

---

### Post by CatKiller on 2009-04-16
> **chaeussinger said:**
> Will do. Thanks for explanation and advice.

No worries. Hope I didn't come across too tetchy. :)

---

### Post by chaeussinger on 2009-04-16
> **CatKiller said:**
> No worries. Hope I didn't come across too tetchy. :)
Don't worry about it.

---

### Post by bendib on 2009-04-19
Oh for the love of god! Install ext2fsd for vista! Either that or use puppy linux to move it back, I know it doesn't whine!

---

### Post by chaeussinger on 2009-04-19
> **bendib said:**
> Oh for the love of god! Install ext2fsd for vista! Either that or use puppy linux to move it back, I know it doesn't whine!
Ain't you the dumbass? The problem is already solved. If you would have paid attention, this is an older thread anyway. 6 days is more than enough to fix an intermediate issue such as this one.

---


---
title: "&quot;Command not found&quot; errors?"
date: 2011-03-22
forum: Desktop Environments
---

### Post by Valkyr333 on 2011-03-22
Hi everyone,

So I'm just finished getting Kubuntu Lucid re-installed, my desktop effects are working again and I'm configuring my Desktop Theme to my favorite, Ubuntu Satanic Edition. SE uses a command for setup called "Sataniconf" with which I've never had problems before, but this time around it returns an error: "Sataniconf: command not found."

Is there a general remedy for "command not found" errors? If so, what is it? If another, more specific angle should be used in my case, what would that be?

Thanks,

-Val

---

### Post by ankspo71 on 2011-03-22
Hi,
Have you tried launching the command by:
```
sh /path/to/Sataniconf
OR
bash /path/to/Sataniconf
```

Only certain directories are allowed to run a script called by name, and when the system tries to search those directories for the command name you have given, it will return the error "command not found" if it can't find it in those directories. This has to do with the PATH environment variable. 

Brief info on PATH:
[File-location related variables]("https://help.ubuntu.com/community/EnvironmentVariables#File-location related variables")

It's possible to add a new directory to your path too, by modifying your personal .bashrc file. Different ways to do this can be seen here:
[https://answers.launchpad.net/ubuntu/+question/3199](https://answers.launchpad.net/ubuntu/+question/3199)

Hope this helps.

---

### Post by Krytarik on 2011-03-22
I just yet checked the website of USE, and there is no mention of those script, instead they advise to change the settings that way:
[http://ubuntusatanic.org/kde-config.php](http://ubuntusatanic.org/kde-config.php)

Greetings.

---

### Post by Valkyr333 on 2011-03-23
Yeah, I've never had a problem with Sataniconf before, it's just happening for the first time now. That same process worked fine the first and second times I did this, and on two different laptops. Apparently, Parker set up the theme with that command to enable easier configuration. Always a plus!

If the command isn't found, does that mean I need to install it?

*Update - I just checked the KDE Website, which says under "announcements" that as of the fourth of this month (March) which was before I got restarted re-installing things, version 4.6.1 came out. "[I]KDE Updates Development Frameworks, Applications and Plasma Workspaces to version 4.6.1"

Is it therefore probable that something about the updated frameworks are incompatible with Ubuntu/Kubuntu SE's "sataniconf" script?
[/I]

---

### Post by Valkyr333 on 2011-03-23
Alright, so I decided to test out my 'updated kde' theory by performing the operations in Gnome instead. The results seem supportive of what I was thinking, I was able to set the login theme and change to the "Satanic" plymouth theme as well. Sataniconf did both these things in Gnome with the same success as I remember. Granted, now I'm looking at the SE Gnome Login Theme instead of the KDE one, but I'm not going to be fussy about it. It looks good enough that I can wait until the SE team updates their theme details for Kubuntu.

Sorry if I might have wasted anyone's time, but I'd love to hear what else if anything that might come to mind for you guys on this topic. Thanks for your responses!

-Val

---

### Post by Krytarik on 2011-03-23
Why don't you just apply the various theme parts the GUI way, like described in the guide I posted the URL of?

---

### Post by Valkyr333 on 2011-03-23
That was actually my first COA after installing the theme. For some reason, selecting the login screen as per the websites instructions for KDE had no effect. The Splash Screen did work, but the login screen and the Satanic Plymouth were a different story. I would have mentioned those things as well, but the thread was/is about the command-not-found error I was getting with sataniconf, so I thought it would be less confusing for everyone involved if I kept to those specifics.

*Edit - They would be considered separate issues, wouldn't they?

---

### Post by Krytarik on 2011-03-23
> **Valkyr333 said:**
> 
*Edit - They would be considered separate issues, wouldn't they?
Exactly.

The original cause of the error message is either like *ankspo71* described, or the incompatibilities mentioned by the author, although I would expect a different error message then.

**EDIT:** Those incompatibilities are obviously also the reason why not all parts of the theme can be applied currently.

---


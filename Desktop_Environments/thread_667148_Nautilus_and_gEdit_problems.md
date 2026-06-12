---
title: "Nautilus and gEdit problems"
date: 2008-01-14
forum: Desktop Environments
---

### Post by shiznatix on 2008-01-14
I have just got back from a 3 week vacation and I updated my Ubuntu to the latest everything but now I have a problem.

All .php files that I have on my hard drive, when attempted to be opened, give me a error about incorrect file types and whatnot. Here is the error:
> The filename "NFW.php" indicates that this file is of type "php document". The contents of the file indicate that the file is of type "PHP script". If you open this file, the file might present a security risk to your system.

That is incredibly annoying and was not happening before but if I do the right-click -> open with text editor everything is fine. The main point about "fine" is that the syntax highlighting is working as always.

The next problem comes with gEdit and mounted ssh connections. I do a lot of my work through the mounted connections with nautilus but now when I open a PHP file through one of these connections it does not complain about incorrect file types or whatever but instead opens gEdit but does not have syntax highlighting anymore!

If someone could help me out with this that would be great because I really need these things to work so that I can do my work.

---

### Post by jackflap on 2008-01-14
What's probably happened is that during the upgrade process, the php shell scripting libraries were installed. This would mean that you can execute php files which could act on your filesystem and system itself. This also probably changed the default application used for opening the files from gEdit.

One thing to note, I personally don't install updates. I will leave a system as-is, and disable the update notifier until I'm ready to spend a weekend updating and sorting out all these types of issues. While I'm waiting till my next update weekend, I spend my time creating images of my hard-drive using SystemRescueCd.

Back to the php problem, try right-clicking on the file, go to Properties, and go through the tabs. Is there a tab which will allow you to select what the default application to open the file is? Perhaps change the default app back to gEdit?

The mounted ssh connections I'm unsure of to be honest. It's a difficult one, perhaps gEdit's options? Also, perhaps consider using Bluefish editor instead of gEdit. It used to be the default Programming/HTML editor in Ubuntu, but they removed it for some reason. You can find it in Synaptic. Otherwise I can't think of anything else.

Alex

---

### Post by shiznatix on 2008-01-15
Well how can I make it so that it does not try to execute php files as scripts from nautilus? The only time I am going to be executing php scripts is from the command line using the php command so how do I turn it off for everything else?

I have looked at the default application for the files but it is still set to gEdit. I am not sure what else I could do.

As for the ssh connections, I have checked all of the settings in gEdit and have not found anything to have changed or to even be amiss. What could possibly make it not use highlighting on those files?

edit: also for the files opening as executables, it also happens when I create a new file and add in the opening and closing php tags. Why oh why.

---

### Post by shiznatix on 2008-01-21
*bump* can anyone help me? At least help me get the files from the ssh connections to open with the highlighting on by default since right now for every file I deal with I have to manually turn the highlighting on for it.

So strange, I wish I knew which update it was and how to make the update go away...

---


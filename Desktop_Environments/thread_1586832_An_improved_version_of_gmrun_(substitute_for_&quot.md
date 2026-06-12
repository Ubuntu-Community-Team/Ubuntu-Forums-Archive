---
title: "An improved version of gmrun (substitute for &quot;Run Application&quot; dialog)"
date: 2010-10-02
forum: Desktop Environments
---

### Post by yashaneiman on 2010-10-02
EDIT: removed the attached source. Will post it properly under the GPL.

Hi all,

One of the things that I found weird in Ubuntu is the lack of a decent Run-Command window, like Winkey+R in MS Windows would give you: a little dialog where you can type a command or a file path and have it opened.
We have the Alt+F2 function, but it won't let you type in a file path.

I found a nice app called gmrun that attempts to address this. It's in the repositories and reasonably documented. Try it.

I found two main problems with gmrun:
1. You need to specify a separate "extension handler" for each file type in a config file. And what about extensionless files, or directories?
2. The extension handlers and autocompletion only work for absolute paths.

So I downloaded the code and made some changes. We now have:
1. All files and directories open by default with the command gnome-open (other than executable binaries, which are executed). This is the same action that happens when you double-click on the file in Nautilus - it gets opened with the appropriate application. You can still edit the config file to set different behavior for specific extensions (I hope). To run an executable script, you have to use Ctrl+Enter.
2. Relative paths work.

I'm using this on my computer for a few days now (mapped to a keyboard shortcut), and it works nicely. We should really have something of the sort in the repos. Trouble is, I don't know the protocol for this sort of situation. The original gmrun is 7 years old, and the programmer doesn't respond to e-mails. What's "the right thing to do" here?

Anyway, I'm attaching my patched up version of the code (no better word for it). To install it, extract the archive, go into the directory in a terminal and run the usual:
```
./configure
make
sudo make install
```It should install under the name gmrun-yasha, without conflicts with the "official" gmrun. I'd be happy if someone tries it and gives me an opinion.

./configure may shout at you that you're missing some libraries. You can install them with Synaptic as packages with names like [LibName]-dev.

Cheers.

---


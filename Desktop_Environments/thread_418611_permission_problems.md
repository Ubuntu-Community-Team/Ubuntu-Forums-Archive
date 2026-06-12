---
title: "permission problems"
date: 2007-04-22
forum: Desktop Environments
---

### Post by Neo2 on 2007-04-22
Hi all,
Newbie still calling! So far I am enjoying Ubuntu enormously, but now hitting the terminal and Nautilus problems. I need to change the etc file in order to install Tor and Privoxy (apparently according to some forum posts!) but of course I can't in Nautilus (won't even let me see what's in the file) and in terminal I can't use sudo either it seems. I typed sudo chmod -r 744 /etc and it told me I had no permission (after asking for password). Any ideas? At this rate I shall never be able to learn how to use the terminal and add anything except Synaptic stuff!

Help!!

Neo

---

### Post by amohanty on 2007-04-22
> sudo chmod -r 744 /etc 

Please don't do that. That is quite dangerous if the wrong numbers are used. To edit any file that you as a user do not have access to:

1. First backup the file:

sudo cp file file.org

2. Use gedit to edit

sudo gedit file

HTH
AM

---

### Post by taurus on 2007-04-22
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Neo2 on 2007-04-23
Thanks all, I'll give it a go. Is there a file of all terminal commands? I'm using Rick Grant's book at the moment and it's good for a newbie like me with reasonable Windows knowledge.

Should I be updating to 7.03 Feisty? Is it stable? Does it detect all hardware like network cards (had an issue on Dapper)?

Neo

---

### Post by amohanty on 2007-04-23
> Thanks all, I'll give it a go. Is there a file of all terminal commands?

Not really. However theres a wonderful command called **apropos** which can be used to find out about commands. For e.g. if I want to find a command to find stuff:

```

08:38 AM: ~
$ apropos find
chkdupexe (1)        - find duplicate executables
find (1)             - search for files in a directory hierarchy
find2perl (1)        - translate find command lines to Perl code
findfs (8)           - Find a filesystem by label or UUID
findsmb (1)          - list info about machines that respond to SMB name queries on a subnet
gst-typefind (1) [gst-typefind-0.10] - print MIME type of file
gst-typefind-0.10 (1) - print MIME type of file
pidof (8)            - find the process ID of a running program.
08:39 AM: ~
$ 

```

HTH
AM

---

### Post by Neo2 on 2007-04-23
Thanks for that! I still have an old version of Dapper on the HD taking up space, can I just delete the partition with Acronis (or similar I suppose to be fair!)? Also the new Feisty, worth the upgrade or not?

Neo

---

### Post by amohanty on 2007-04-23
> **Neo2 said:**
> Thanks for that! I still have an old version of Dapper on the HD taking up space, can I just delete the partition with Acronis (or similar I suppose to be fair!)? Also the new Feisty, worth the upgrade or not?

Neo

I am still on edgy, by default unless there's some really pressing feature in a new version I don't upgrade on my daily use machine. I do have a tester machine that I play around with. If you like eye candy, Feisty is definitely worth it. There are some improvements, but nothing that will make me move towards it for the next 6-8 months or so. But that's just me.

If you don't have any data and are using ubuntu, yes you can blow away the parition, or you can just reformat it and reuse the space.

AM

---


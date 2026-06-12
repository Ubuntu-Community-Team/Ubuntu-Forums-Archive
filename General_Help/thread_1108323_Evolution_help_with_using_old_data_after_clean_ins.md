---
title: "Evolution: help with using old data after clean install"
date: 2009-03-27
forum: General Help
---

### Post by megamania on 2009-03-27
This should be an easy one for some of you... or I hope so.

I just made a clean install of Ubuntu. I wanted the system to be *clean*, so I also started with a clean home.

After that, I copied from my backup the configuration files/.directories for the various programs. Everything works fine, except for Evolution.

I copied the .Evolution directory to /home, but Evolution keeps insisting that it's being run for the first time, and forces me to enter my email data.
After that, I can see the calendar and contacts, but my email configuration is not there (I use Imap servers).

I think there's some other folder/configuration file (maybe in .gnome?) that I need to copy. Since I have a full backup of my home, it's just a matter of understanding *what* to copy.
I searched for "evolution" on my computer, but didn't find anything.

Any ideas?

---

### Post by megamania on 2009-03-28
anybody?

---

### Post by dcstar on 2009-03-28
> **megamania said:**
> This should be an easy one for some of you... or I hope so.

I just made a clean install of Ubuntu. I wanted the system to be *clean*, so I also started with a clean home.

After that, I copied from my backup the configuration files/.directories for the various programs. Everything works fine, except for Evolution.

I copied the .Evolution directory to /home, but Evolution keeps insisting that it's being run for the first time, and forces me to enter my email data.
After that, I can see the calendar and contacts, but my email configuration is not there (I use Imap servers).

I think there's some other folder/configuration file (maybe in .gnome?) that I need to copy. Since I have a full backup of my home, it's just a matter of understanding *what* to copy.
I searched for "evolution" on my computer, but didn't find anything.

Any ideas?

Either simply copy all of the hidden files from your saved /home directory, or pick out the .gnome* and .gconf* folders as well as the .evolution folder.

You can go into those old folders and try and copy all evolution data, but that can be messy.

It would also be better to have done an Evolution backup and then restored that as it (AFAIK) contains all the settings as well as data.

---

### Post by megamania on 2009-03-30
> **dcstar said:**
> You can go into those old folders and try and copy all evolution data, but that can be messy.

It would also be better to have done an Evolution backup and then restored that as it (AFAIK) contains all the settings as well as data.
In fact, I tried to copy the evolution data from the gconf folder, but that was... messy.

I didn't think about the backup/restore option because I thought it was only needed to move the files to a different computer. My bad.

I just re-configured everything from scratch - I'm using Imap, so I have no problem with re-importing mail...

Thanks!

---

### Post by LuigiAntoniol on 2009-03-31
I have a similar problem.

Have recently upgraded 8.04 to 8.10.

In 8.04, I used Evolution backup to copy everything from Evolution into a backup file (emails, calendar, contacts).

I successfully imported this file into Evolution that comes with 8.10, but now I can only open Evolution in terminal using "**sudo evolution**".  The taskbar launcher doesn't work and neither does the menu launcher.

Have I missed something in the permissions? :confused:

---

### Post by megamania on 2009-03-31
> **LuigiAntoniol said:**
> In 8.04, I used Evolution backup to copy everything from Evolution into a backup file (emails, calendar, contacts).

I successfully imported this file into Evolution that comes with 8.10, but now I can only open Evolution in terminal using "**sudo evolution**".  The taskbar launcher doesn't work and neither does the menu launcher.

Have I missed something in the permissions? :confused:
Did you change your user name with the new install?

---

### Post by LuigiAntoniol on 2009-03-31
@megamania
"Did you change your user name with the new install? "

No.  I only entered one user at installation.  No changes or addition to users after that.

After I've launched Evolution from the terminal, everything works perfectly.

When I click on the launcher icons, I get a very fast smallish pop-up that disappears too quickly for me to see what it says.

Any ideas on what I could have done wrong?

---

### Post by megamania on 2009-03-31
> **LuigiAntoniol said:**
> 
No.  I only entered one user at installation.  No changes or addition to users after that.

Sorry, I wasn't clear. I was wondering if for your new install you used a different name from your old install.

For example:
Old machine: username=Luigi
New machine: username=Antonio

In that case, it may be possible that Evolution imported the files with the permissions for Luigi, while the current user is Antonio.

As I said, it's just a guess.

---

### Post by LuigiAntoniol on 2009-03-31
> **megamania said:**
> Sorry, I wasn't clear. I was wondering if for your new install you used a different name from your old install.

For example:
Old machine: username=Luigi
New machine: username=Antonio

In that case, it may be possible that Evolution imported the files with the permissions for Luigi, while the current user is Antonio.

As I said, it's just a guess.

Oh, I see what you mean.

Also no.  The username has always been luigiantoniol.

The only thing that did change was the name of the computer, but that shouldn't be a problem.

Is it possible to change those permissions?

Alternatively, I could simply change the launcher with a terminal command "sudo evolution".

Funny thing is this; I never get asked for a password when I do the "sudo evolution" in terminal.

---

### Post by megamania on 2009-04-03
> **LuigiAntoniol said:**
> Is it possible to change those permissions?

did you try
sudo chown -R luigiAntoniol /home/luigiAntoniol/.evolution/
?

---

### Post by LuigiAntoniol on 2009-04-08
> **megamania said:**
> did you try
sudo chown -R luigiAntoniol /home/luigiAntoniol/.evolution/
?

No.  Not very familiar with the command line.  Will try that and report back.

Thanks for the tip.

---

### Post by LuigiAntoniol on 2009-04-08
> **megamania said:**
> did you try
sudo chown -R luigiAntoniol /home/luigiAntoniol/.evolution/
?

No luck.

I also tried sudo nautilus to change the permissions that way, also no luck.

The sudo evolution works very well.  Maybe I should just stick with what works.

---

### Post by megamania on 2009-04-08
> **LuigiAntoniol said:**
> No luck.

Last try - do the same thing with the .gconf directory:
```
sudo chown -R luigiAntoniol /home/luigiAntoniol/.gconf/
```

---

### Post by LuigiAntoniol on 2009-04-10
> **megamania said:**
> Last try - do the same thing with the .gconf directory:
```
sudo chown -R luigiAntoniol /home/luigiAntoniol/.gconf/
```

Still nothing.

I get a quick flash of something in a small dialogue box only once, and every time thereafter, the icon flashes, but nothing happens.

I also did "**sudo chown -R luigiantoniol /home/luigiantoniol/.evolution/**" afterwards to see if changing the permissions on the conf folder would affect the permissions of the .evolution folder.  Still nothing.

Do you think something might have got corrupted somewhere?

The sudo evolution works.  Have created a launcher for the desktop and am using that to access evolution.

---

### Post by megamania on 2009-04-10
I'm running out of ideas.

You could post the output you get when running evolution (without sudo) from the terminal...

---

### Post by LuigiAntoniol on 2009-04-10
> **megamania said:**
> I'm running out of ideas.

You could post the output you get when running evolution (without sudo) from the terminal...

**_Evolution without sudo_**:

luigiantoniol@Antoniol:~$ evolution

(evolution:22528): camel-WARNING **: camel_exception_get_id called with NULL parameter.

GLib-ERROR **: /build/buildd/glib2.0-2.18.2/glib/gmem.c:136: failed to allocate 31942090464 bytes
aborting...
Aborted
luigiantoniol@Antoniol:~$

---

### Post by megamania on 2009-04-11
it's a bug: [https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/291430](https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/291430)

This appears to fix it:
> 
I've been suffering the same problem since upgrade to Ibex from Hardy. I managed to fix it by temporarily moving my ~/.evolution folder.

1) mv ~/.evolution ~/.evolution.bak
2) Started evolution with no problems with fresh settings
3) rm -rf ~/.evolution
4) mv ~/.evolution.bak ~/.evolution


---

### Post by LuigiAntoniol on 2009-04-11
> **megamania said:**
> it's a bug: [https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/291430](https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/291430)

This appears to fix it:
I've been suffering the same problem since upgrade to Ibex from Hardy. I managed to fix it by temporarily moving my ~/.evolution folder.

1) mv ~/.evolution ~/.evolution.bak
2) Started evolution with no problems with fresh settings
3) rm -rf ~/.evolution
4) mv ~/.evolution.bak ~/.evolution 

[CENTER][SIZE="4"]**[COLOR="Red"]SOLVED[/COLOR]**!!:guitar:[/SIZE]

I thought I was going crazy.:cry::twisted:

What I can't understand is why it worked as **sudo**, but not under normal conditions.

**Thanks a million!!**

Now I can get back to work properly.[/CENTER]

---

### Post by megamania on 2009-04-11
> **LuigiAntoniol said:**
> **Thanks a million!!**
Glad I could help! ):P

---


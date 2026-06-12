---
title: "Is the Administrator option working yet or KDE Control Panel?"
date: 2005-05-26
forum: Desktop Environments
---

### Post by vvu on 2005-05-26
Can someone tell me if the Kubuntu team or Kubuntu in general has been fixed yet - pertaining to the non working Administrator option in KDE's Control Panel?

For example, if I am in the KDE Control Panel and need to change something that requires root access - there's an Administrator button - BUT that button does not work since it keeps bringing me back to the main screen.

Please let me know the staus of this.

Thank you.

---

### Post by vanshark on 2005-05-26
[QUOTE=vvu]Can someone tell me if the Kubuntu team or Kubuntu in general has been fixed yet - pertaining to the non working Administrator option in KDE's Control Panel?

For example, if I am in the KDE Control Panel and need to change something that requires root access - there's an Administrator button - BUT that button does not work since it keeps bringing me back to the main screen.

Please let me know the staus of this.

Thank you.[/QUOTE]

this worked for me:

sudo kwrite /etc/sudoers

(to the bottom of the file add this line)

system_username ALL=(ALL) ALL

(save file)

here's what mine looks like

> 
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults !lecture,tty_tickets,!fqdn

# User privilege specification
root ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

system_username ALL=(ALL) ALL


I believe I had to reboot for the settings to take effect...hope this helps!

Jim

---

### Post by philipacamaniac on 2005-05-27
Do you know of any security leaks this might cause? If it is safe, this is the bug fix we've been looking for.

---

### Post by fdoving on 2005-05-27
[QUOTE=philipacamaniac]Do you know of any security leaks this might cause? If it is safe, this is the bug fix we've been looking for.[/QUOTE]
 You should rather add your user to the admin group.
From konsole: 
'sudo adduser username admin'

By default the user you add during install is already a member of the admin group.
You can check this by running 'id' in konsole.

- Frode

---

### Post by bigbadblo on 2005-05-27
Experiencing the same problems as stated above.  Operating as the admin, as well as trying the fixes named here as well.  Still no luck.  I'm new to Linux -- is there a terminal command to initialize my ethernet card?

Thx

blo

---

### Post by philipacamaniac on 2005-05-27
[QUOTE=fdoving]You should rather add your user to the admin group.
From konsole: 
'sudo adduser username admin'

By default the user you add during install is already a member of the admin group.
You can check this by running 'id' in konsole.

- Frode[/QUOTE]

Actually, my user has always been in the admin group (as implied by the default behaviour).

As for this system_username fix, it doesn't seem to be working as well on another Kubuntu machine that I've tried. I'm still testing different scenarios.

---

### Post by vanshark on 2005-05-28
[QUOTE=philipacamaniac]Do you know of any security leaks this might cause? If it is safe, this is the bug fix we've been looking for.[/QUOTE]

I found the system_name solution via google a few weeks ago. As far as security leaks I have no information. I've used this solution on 2 desktop PC's as well as my laptop and it's worked each time. 

Jim

---

### Post by Xian on 2005-05-28
You could just open the Control Panel with Admin rights by entering this command from the KDE Start Menu panel > Run Command:

kdesu kcontrol

---

### Post by vvu on 2005-05-28
You could, but that is a workaround and prefer the actual solution.

---

### Post by recover82 on 2005-05-28
agreed.  i guess a work around is better than nothing for the time being..but with the next official release still 5 months away?  there should be a patch or something for this issue.

---

### Post by bhrich902 on 2005-05-28
i may have found the quirk, if u open kmenuedit and click on the control center entry, in the command section for it you'll see that it goes kcontrol followed by somem other flags to it, if you remove the tag and just have it say kcontrol it should be fixed. let me know if it works for some.

---

### Post by improverrr on 2005-05-29
[QUOTE=bhrich902]i may have found the quirk, if u open kmenuedit and click on the control center entry, in the command section for it you'll see that it goes kcontrol followed by somem other flags to it, if you remove the tag and just have it say kcontrol it should be fixed. let me know if it works for some.[/QUOTE]

i thought it worked at first.  But it turns out it only works sometimes.  this is what I did to test it:

[list]
[*]it was working with and without the menu changed, so i restored back to default setting and rebooted
[*]once rebooted, tried it, no work... removed the tag...it worked...thought you were on to something..
[*]rebooted with out the tag there, no worky...
[/list] 

so i just changed it to read: "kdesu kcontrol" so know upon opening, it prompts for a password.  I think I like this option anways!  \\:D/ 

Thanks for trying though!  :razz:

---

### Post by philipacamaniac on 2005-05-29
[QUOTE=improverrr]so i just changed it to read: "kdesu kcontrol" so know upon opening, it prompts for a password.  I think I like this option anways!  \\:D/ 
[/QUOTE]

If you do that, you won't be able to make changes to your personal settings, such as your visual theme, icons, fonts, program associations, etc. 
Opening as root (kdesu) only changes system-wide options. Not a solution to this problem, only an annoying workaround.

---

### Post by improverrr on 2005-05-29
[QUOTE=philipacamaniac]If you do that, you won't be able to make changes to your personal settings, such as your visual theme, icons, fonts, program associations, etc. 
Opening as root (kdesu) only changes system-wide options. Not a solution to this problem, only an annoying workaround.[/QUOTE]

intresting.  good catch.  I guess I will just have to have 2 accesses to kcontrol.  yes annoying workaround, but atleast there is a workaround.  this is a minor problem compared to me not being able to get streaming radio in kaffeine... ](*,) 

thanks again!

---

### Post by Mez on 2005-05-30
I've found a couple of times that it doesnt work becuase of someonthing else runnning in the background trying to do the same thing, or an uncvlean konq exit.

Normally a restart of X fixes it (ctrl alt backspace)

---

### Post by kubuntuuser on 2005-06-15
Upgrading to kde3.4.1 will not fix this problem. 

See the KDE change log here

[http://www.kde.org/announcements/changelogs/changelog3_4to3_4_1.php](http://www.kde.org/announcements/changelogs/changelog3_4to3_4_1.php)

---

### Post by jshein on 2005-08-29
OK.

Here's my 2 cents.

I have had this problem with Kubuntu since it's release, and have been doing the workaround with kdesu.

Here's an idea though.

I just received my Ubuntu CD shipment ( after 5 months waiting ) and installed this for a client of mine. As I prefer giving new users to linux a KDE environment, I installed all nescesary packages through synaptic. 

Lo and behold, the administrator function works.

Maybe try this:

If someone out there has 2 identical machines. Install one with Ubuntu and add all KDE applications. install the other machine with Kubuntu, and add Gnome packages.

Now run a file system comparison against the two systems ( diff ). Examine the results and see what the differences are ni files that could cause this loop.

I would have already done this if I had 2 identical machines that were not in use.

---


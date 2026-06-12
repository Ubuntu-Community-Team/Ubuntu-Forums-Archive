---
title: "LC_TIME not respected in all applications"
date: 2008-08-17
forum: Desktop Environments
---

### Post by andrewski on 2008-08-17
My general locale is en_US.UTF-8, but as I prefer 24-hour clocks and starting my week on Monday, I'd like to use en_DK.UTF-8 for my LC_TIME environment variable.

However, it doesn't seem to be working. `zenity --calendar` works (shows the calendar starting on Monday), but Evolution and GNOME Panel do not. `date` and `zenity --filechooser` show the date in 24-hour format, but Nautilus, Pidgin, and Tomboy (as well as a GTK+ filechooser from any applications) do not.

I wondered if it might be a terminal thing (seems to favor applications started in a terminal), but that's not the case: I can start any of those applications from a terminal and it won't make a difference.

Lastly, running `LC_TIME=en_DK.UTF-8 evolution` or whatnot *does* work, but only for that one session.

Any ideas what I'm doing wrong?

---

### Post by pauper on 2008-08-17
> **andrewski said:**
> Lastly, running `LC_TIME=en_DK.UTF-8 evolution` or whatnot does work, but only
for that one session.

Add "export LC_TIME=en_DK.UTF-8 evolution" to ~/.bashrc--should work for any
next session.

---

### Post by andrewski on 2008-08-18
Sorry, that's what I already have (minus the `evolution`, was that intentional?). I use ZSH as my shell, so it's my .zshrc instead of .bashrc (and I've also tried .zshenv from one particular howto I read).

---

### Post by andrewski on 2008-09-06
To be more specific: 
Currently I have `export LC_TIME="en_DK.UTF-8"` in .zshenv, .zprofile, .zshrc and .zlogin (the four files used in various ways by zsh when starting, as per [http://zsh.dotsrc.org/FAQ/zshfaq03.html#l19](http://zsh.dotsrc.org/FAQ/zshfaq03.html#l19)).

Applications I start from GNOME Terminal or the GNOME Run box (Alt+F2) (e.g. `date`, `zenity --calendar`, Evolution) will use the correct date/time settings.

However, the calendar is incorrect on the GNOME panel, and any application I start from the menu (or GNOME Do, for example) uses the incorrect locale.

So it seems GNOME, at some level, is not picking up my environment variable.

---

### Post by Brucevdk on 2008-12-01
Came across this post while Googling. 

I still haven't found out how one can set user specific environment variables that programs not started from a Bash shell also know about (the problem here lies in the fact that ~/.bashrc, ~/.profile etc. aren't always parsed). However, if you don't mind you can set system wide environment variables that GDM etc. will also know about in /etc/environment. Hope that helps.

---

### Post by andrewski on 2008-12-02
Thanks, that does seem to work. Odd though, and it might be confusing for the fiancé.... :)
I'm thinking of filing a bug, unless you have some insight as to why it's not one?

---

### Post by andrewski on 2008-12-09
OK, bug filed: [https://bugs.launchpad.net/bugs/306591](https://bugs.launchpad.net/bugs/306591). Bruce, thanks again for the tip! And hopefully we'll see what comes of that bug report.

---

### Post by maxclaus on 2009-03-06
Hi all,
as i've a similar problem with date/time format here is what i found until now:

Searching in the forum and the archive i found a solution to change the systems date/time format at [http://ubuntuforums.org/showthread.php?t=193916&highlight=date+format](http://ubuntuforums.org/showthread.php?t=193916&highlight=date+format), which works pretty good (Ubuntu 8.04) and displays the prefered/changed formats in nautilus perfectly. Maybe the mentioned link can help with Your problem. 

However the measure doesn't solve the date/time format problem during file browsing:  the commands 'open', 'save as' etc. in other applications (e.g. Gedit, Gimp, etc.) which open a browsing tool (i don't know if these 'browsers'are integrated parts of the regarded applications, gnome, nautilus or whatever) still deliver data formats as 'today', 'yesterday', 'monday'...etc, but not the prefered format installed in /usr/share/i18n/locales + /etc/environment according to the a.m. link and displayed in nautilus.

As i've already changed the format for gnomes clock-applet and the gnome-commander (both working correctly), obviously these browsing tools use another data base for the format as Nautilus does.

Maybe someone of the visitors of this thread has an idea where/how to change these date/time formats.

---

### Post by andrewski on 2009-03-06
> **maxclaus said:**
> Searching in the forum and the archive i found a solution to change the systems date/time format at [http://ubuntuforums.org/showthread.php?t=193916&highlight=date+format](http://ubuntuforums.org/showthread.php?t=193916&highlight=date+format), which works pretty good (Ubuntu 8.04) and displays the prefered/changed formats in nautilus perfectly. Maybe the mentioned link can help with Your problem. 
Not exactly what I'm discussing here, but thanks for sharing. I don't need to create a new locale, just need to apply my existing one to all applications.

> **maxclaus said:**
> However the measure doesn't solve the date/time format problem during file browsing:  the commands 'open', 'save as' etc. in other applications (e.g. Gedit, Gimp, etc.) which open a browsing tool (i don't know if these 'browsers'are integrated parts of the regarded applications, gnome, nautilus or whatever) still deliver data formats as 'today', 'yesterday', 'monday'...etc, but not the prefered format installed in /usr/share/i18n/locales + /etc/environment according to the a.m. link and displayed in nautilus.

As i've already changed the format for gnomes clock-applet and the gnome-commander (both working correctly), obviously these browsing tools use another data base for the format as Nautilus does.
Sounds like one of two things: either you'll want to change your Display preference in Nautilus' preferences (Edit | Preferences | Display tab) or you're experiencing the same problem as I: namely that your LC_TIME is not being applied where you set it. (Where did you set yours?)

---

### Post by maxclaus on 2009-03-06
Maybe an explanation is necessary: as i'm relatively new to Linux/Ubuntu (~6 months) => i'm not really familiar with the system. Therefore i followed the instructions of the mentioned link nearly 1:1, with one exception: as i'm basically using for the locale 'de_DE' (basic installation of the system) i recognized, that the original lines 

'% Appropriate date representation (%x)
%       "%m/%d/%Y"
d_fmt   "<U0025><U006D><U002F><U0025><U0064><U002F><U0025><U0059>"

already cover my intensions. But the lines 

% Appropriate date and time representation (%c)
%	"%a %d %b %Y %T %Z"
d_t_fmt "<U0025><U0061><U0020><U0025><U0064><U0020><U0025><U0062><U0020><U0025><U0059><U0020><U0025><U0054><U0020><U0025><U005A>"

didn't, as they exactly contain what i don't prefer. So i changed them to my wishes and transfered the new 'custom' file per '$ sudo localedef -f UTF-8 -i custom custom.UTF-8' to UTF-8 

and then added in

/etc/environment:
LC_TIME="custom.UTF-8"

as recommended by 'Brocco'. The result (for me) was good, as the first time during investigations i've got a positive echo (in nautilus). Besides: the fact, that commands as 'save as' etc. don't follow the general installation reminds me a bit to the behaviour of Windows (XP_SP2): even if all other settings are 'perfect': i never succeeded to get the same commands ('save as'...) to remember my settings (long file list, remember the last path, sorting by date....), not even in the same session and MS applications only. Other applications (e.g full version ADOBE software): same thing (reasons enough to try a new system)
So, reading Your thread i assumed a similar problem, but maybe i'm wrong.

---

### Post by andrewski on 2009-03-06
> **maxclaus said:**
> So, reading Your thread i assumed a similar problem, but maybe i'm wrong.
Not the same issue here. You could start a new thread or search for existing threads about that, but it sounds like you applied your locale globally (with the `sudo localedef` command) so you should be good.

---

### Post by HadroLepton on 2009-04-10
a copy from my answer at launchpad for those coming to this thread from google or otherwise

[https://answers.launchpad.net/questions/60699](https://answers.launchpad.net/questions/60699)

in response to the original question:

i have this done in my .profile file. here are the relevant lines from my .profile file:

## everything is set to german (datum, uhrzeit, komma, euro)
export LANG=de_DE.utf8
## programs still talk to me in english
export LC_MESSAGES=en_US.utf8
## sort order based on ASCII order
export LC_COLLATE=C

some background explanation: gdm parses .profile (see /etc/gdm/Xsession). gdm also parses .xprofile, but i wanted the LC_* settings for bash and for gnome, so i put it in .profile. the .profile file is read by gnome and by bash if bash is started as a login shell (check the bash manual for an explanation of what a login shell is, generally if you just typed your username and password then it is a login shell). in the standard .profile file provided by ubuntu there is a condition which checks wether .profile is read by bash, in which case it also reads .bashrc, if not then it will not include .bashrc, so gdm will not parse .bashrc.

here is me being smartypants: bash will not read .profile if it finds a .bash_profile first (check the bash manual about startup files). i created a .bash_profile which reads .profile and then .bashrc. this way gnome can read .profile all it wants and won't collide with bash. bash itself will not read .profile because it finds a .bash_profile, which tells bash to read .profile. it's a bit weird but it feels better this way then the way ubuntu (or debian) did it with the condition in .profile.

---

### Post by Lieter on 2009-04-23
I've done the same

## everything is set to dutch
export LANG=nl_NL.utf8
## programs still talk to me in english
export LC_MESSAGES=en_US.utf8

however. ccsm is partly dutch now...

And if i set
export LC_TIME=nl_NL.utf8

and nothing else the time in gnome-do isn't set correctly, but the time in evolution and nautilus are.. It kinda bugs me... Can you why this is?

---

### Post by andrewski on 2009-04-24
Lieter, Mono applications do not apply the LC_TIME correctly: [https://bugzilla.novell.com/show_bug.cgi?id=320045](https://bugzilla.novell.com/show_bug.cgi?id=320045).
Sounds like yours is about as good as it will get right now.

---


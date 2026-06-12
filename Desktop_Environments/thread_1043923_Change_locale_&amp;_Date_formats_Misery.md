---
title: "Change locale &amp; Date formats Misery"
date: 2009-01-19
forum: Desktop Environments
---

### Post by tokyoahead on 2009-01-19
Hi,

My system clock shows "Mon Jan 19, 9:19", which is fine because its 24hrs but bad because I dont need the weekday. 09/01/19 would be perfect.

Additionally, Thunderbird shows me this:
Monday, January 19, 2009 09:19 AM 
Which is stupid because 
[LIST]
[*]its different from the desktop time
[*]its 12hr format
[*]its much much too long
[/LIST]

Then, Lotus Notes (8.5 debian, not WINE)
Shows me the following:
01/19/2008 | AM 09:19
Which is also stupid because:
[LIST]
[*]its also 12HR
[*]its slightly different than thundebrird (AM in front instead of behind the time)
[*]its MM/DD/YYYY instead of a prefered YYYY/MM/DD or DD/MM/YYYY at least
[/LIST]

How can I unify those? I found out that I have to "change locale". There is a manual at [https://help.ubuntu.com/community/LocaleConf](https://help.ubuntu.com/community/LocaleConf)
but the localeconf package seems to be unavailable since gutsy?

so how do I change the locale? How can I make the applications look even remotely the same?

thanks,

Oliver

---

### Post by adamlau on 2009-01-19
Verify and reconfigure your timezone:

```
dpkg-reconfigure tzdata
```

Applications typically have their own syntax and display format.

---

### Post by tokyoahead on 2009-01-20
> **adamlau said:**
> Verify and reconfigure your timezone:


thanks. but this does not change the time format at all - only the time itself.

Oliver

---

### Post by samuli64 on 2009-02-04
I have a similar problem with Lotus Notes 8.5 debian install. American date format in my calendar is very annoying.

---

### Post by ugutugut on 2009-10-11
I second it, use Lotus Notes 8.5 in Jaunty 9.04, I have similar date format problem. It shows mm/dd/yyyy, and I can't find a way to change it to dd/mm/yyyy. 
Anybody out there know how to solve this problem? thank you in advance.

---

### Post by ugutugut on 2009-10-15
ok, I've solved my problem, now my Lotus Notes can display date in format dd/mm/yyyy. What I've done was modifying LC_TIME value to en_GB.
In my understanding, GB (British) date format is dd/mm/yyyy.
   1) gksudo gedit /etc/environment
   2) add folowing line
     LC_TIME="en_GB.utf8"

Save and reboot.

---


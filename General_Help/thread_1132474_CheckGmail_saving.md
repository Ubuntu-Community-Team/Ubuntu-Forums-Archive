---
title: "CheckGmail saving"
date: 2009-04-21
forum: General Help
---

### Post by brandoncolorado on 2009-04-21
I am using Ubuntu 9.04 UNR.  I have checkgmail installed from the add/remove screen.  I save my password and check "save password," but it seems that about 4/5 restarts the program doesn't save my password.  Is this a problem with the program, or is there some setting in Ubuntu I need to change?

Thanks

---

### Post by lovinglinux on 2009-04-21
I had the same problem when I used checkgmail. I'm using [Gmail Notifier](https://addons.mozilla.org/en-US/firefox/addon/173) for Firefox now.

---

### Post by beforefirstlight on 2009-04-22
I have exactly the same problem and I didn't find any solution! :(

---

### Post by brandoncolorado on 2009-04-22
It seems to me that the CheckGmail project may be dead.  I really don't like the popup notifier for gmail-notify, but that may have to do.

---

### Post by MyR on 2009-04-25
Well I have not experienced this problem.  One hack I can think of is to open up ~/.checkgmail/prefs.xml with a text editor and make sure save_passwd="1" and that your password is saved (preferrably encrypted).  Then if everything looks OK you can set the file permissions to read-only.
I haven't tried any of this so no guarantees.

my file looks like this (using checkgmail v1.12.1svn)
> <opt archive_as_read="0"
     atomfeed_address="mail.google.com/mail/feed/atom"
     delay="60000"
     gmail_command="opera -newpage %u"
     language="English"
     nomail_command=""
     notify_command="aplay ~/Music/mail.wav"
     passwd="xxxxx"
     popup_delay="6000"
     save_passwd="1"
     show_popup_delay="250"
     time_24="0"
     user="xxxx">
  <label_delay></label_delay>
</opt>

peace

---

### Post by brandoncolorado on 2009-05-15
Mine is similar,

<opt archive_as_read="0"
     atomfeed_address="mail.google.com/mail/feed/atom"
     delay="120000"
     gmail_command="firefox %u"
     language="English"
     passwd="xxxxxx"
     popup_delay="6000"
     save_passwd="1"
     show_popup_delay="250"
     time_24="0"
     user="myusername">
  <label_delay></label_delay>
</opt>

---

### Post by brandoncolorado on 2009-05-15
and here is a screenshot of the permissions on that file:

---

### Post by brandoncolorado on 2009-05-15
I think I may have found the source of the problem:

After a restart, when I run checkgmail in terminal, I get this error:

"Use of uninitialized value in subroutine entry at /usr/share/perl5/Crypt/Simple.pm line 144."

---

### Post by MyR on 2009-05-15
> **brandoncolorado said:**
> I think I may have found the source of the problem:

After a restart, when I run checkgmail in terminal, I get this error:

"Use of uninitialized value in subroutine entry at /usr/share/perl5/Crypt/Simple.pm line 144."

well you can reinstall or remove libcrypt-simple-perl and see what happens :\ don't know what the problem is.

---

### Post by feroxy on 2009-08-03
I have a fix for this that works for me. The problem seems to arise because of the existence of a "pan0" interface when "ifconfig -a" is run, which seems to be some sort of bluetooth related item (it was there by default in my 9.04 install). The problem is that checkgmail uses the mac (HWaddr) address of this item as part of its password encryption (rather than say the mac address of a physical eth or wlan adapter you may have installed), but this mac address changes on almost every reboot.

I fixed it by changing one line in the checkgmail script:
- close down checkgmail if running
- open /usr/bin/checkgmail using sudo and your preferred editor (eg "gksudo gedit /usr/bin/checkgmail")
- find the line that reads: (on line 163)
```
my $mac = `$ifconfig_path -a | grep -m 1 HWaddr | sed 's/ //g' | tail -18c`;
```and change it to:
```
my $mac = `$ifconfig_path -a | grep -m 1 -Ee '^(eth|wlan)' | sed 's/ //g' | tail -18c`;
```- save then restart checkgmail. It should start saving the password now (until your kernel is upgraded, in which case I think it will ask again)

Hopefully this works for you as it has for me. You could probably also solve this by disabling pan0, but I felt this was easier for me.

---

### Post by viktor.pec on 2009-08-17
Good job. Works for me.

---


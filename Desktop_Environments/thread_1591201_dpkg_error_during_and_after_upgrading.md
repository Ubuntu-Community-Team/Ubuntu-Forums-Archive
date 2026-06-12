---
title: "dpkg error during and after upgrading"
date: 2010-10-08
forum: Desktop Environments
---

### Post by james_xxx on 2010-10-08
While upgrading to Maverick this afternoon, I got what were hundreds of these errors:

```
warning, in file '/var/lib/dpkg/status' near line 51010 package 'virtualbox-3.1':                                                                                                                                    
 error in Version string '3.1.6-59338_Ubuntu_karmic': invalid character in revision number                                                                                                                           
warning, in file '/var/lib/dpkg/status' near line 51011 package 'virtualbox-3.1':                                                                                                                                    
 error in Config-Version string '3.1.6-59338_Ubuntu_karmic': invalid character in revision number                                                                                                                    
warning, in file '/var/lib/dpkg/status' near line 51064 package 'virtualbox-3.0':                                                                                                                                    
 error in Version string '3.0.12-54655_Ubuntu_karmic': invalid character in revision number                                                                                                                          
warning, in file '/var/lib/dpkg/status' near line 51065 package 'virtualbox-3.0':                                                                                                                                    
 error in Config-Version string '3.0.12-54655_Ubuntu_karmic': invalid character in revision number                                                                                                                   
warning, in file '/var/lib/dpkg/available' near line 52108 package 'virtualbox-3.1':                                                                                                                                 
 error in Version string '3.1.6-59338_Ubuntu_karmic': invalid character in revision number                                                                                                                           
warning, in file '/var/lib/dpkg/available' near line 52159 package 'virtualbox-3.0':                                                                                                                                 
 error in Version string '3.0.12-54655_Ubuntu_karmic': invalid character in revision number
```

Since upgrading, I see this error over and over, at any time any package management is being undertaken.

Anyone have a suggestion?

---

### Post by james_xxx on 2010-10-09
The problem seems to be that the underscore has become at some point an illegal character in Debian package names.

What worked for me was just manually editing the offending lines in the specified files, changing all underscores to tildes.

Now I no longer get all of these errors.

I hope there are other that are helped by this info!

---

### Post by Envy Life on 2010-10-10
Thanks for that solution... I could not figure out what invalid character it was complaining about!

---

### Post by cdotto on 2010-10-12
Thank you, [james_xxx]("http://ubuntu-ky.ubuntuforums.org/member.php?u=118811"). The same problem here. SOLVED! Thanks a lot.

---

### Post by kaveraj on 2010-10-14
a much more elegant solution
> sudo dpkg --clear-avail

source: [https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/636586](https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/636586)

---

### Post by james_xxx on 2010-10-14
That would indeed be a MUCH more elegant solution.

Although the way I went about things worked, I wish I had known about this method when the problem first appeared.

---

### Post by landrew on 2010-10-22
> **kaveraj said:**
> a much more elegant solution


source: [https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/636586](https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/636586)

Sadly, using "dpkg --clear-avail" only removes the warnings about the "/var/lib/dpkg/available" lines.  The warnings about "/var/lib/dpkg/status" are still generated whenever package operations occur.

I edited the /var/lib/dpkg/status file, and changed the underscore characters to tilde characters as the OP suggested, and that appears to have eliminated the warning messages here.

-L'andrew

---

### Post by schworak on 2010-11-14
I used both methods just to be safe. The warnings are gone but won't the tilde in the name cause some other issue down the road? I mean, won't the package name miss-match the real package name now? Or is the tilde a special character that matches anything?

I did it and it worked but I don't understand why it doesn't break something else.

Thnks!

---

### Post by gtgrover on 2011-01-14
Thanks, this solved my problems too! :D

---

### Post by SvenRieke on 2011-02-24
I had the same warning messages from old VirtualBox installations, but instead of altering the */var/lib/dpkg/status* by hand, I just purged the old packages:

[FONT="Lucida Console"]sudo aptitude purge virtualbox-2.2
sudo aptitude purge virtualbox-3.0[/FONT]

The corresponding entries disappeared from the status file, and my 3.2 version does still work.

---

### Post by kngharv on 2011-03-24
> **SvenRieke said:**
> I had the same warning messages from old VirtualBox installations, but instead of altering the */var/lib/dpkg/status* by hand, I just purged the old packages:

[FONT="Lucida Console"]sudo aptitude purge virtualbox-2.2
sudo aptitude purge virtualbox-3.0[/FONT]

The corresponding entries disappeared from the status file, and my 3.2 version does still work.


This is by far the BEST solution.  It is much better than hand-editing config file of any sort.  Thank you so much!

---

### Post by afrodeity on 2011-06-07
> **landrew said:**
> Sadly, using "dpkg --clear-avail" only removes the warnings about the "/var/lib/dpkg/available" lines.  The warnings about "/var/lib/dpkg/status" are still generated whenever package operations occur.

I edited the /var/lib/dpkg/status file, and changed the underscore characters to tilde characters as the OP suggested, and that appears to have eliminated the warning messages here.

-L'andrew

Does one do a simple change and replace on every _ or how?

---


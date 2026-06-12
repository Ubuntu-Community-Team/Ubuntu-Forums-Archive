---
title: "Thunderbird not opening link"
date: 2008-11-29
forum: Desktop Environments
---

### Post by asearle on 2008-11-29
I have an installation of Kubuntu 8.04 with Firefox (3.0.4) and Thunderbird (2.0.0.18) and find that url links including in e-mails will not open automatically in Firefox from Thunderbird.

I have set Firefox as the default browser in 'default applications' and in 'Firefox' advanced settings but this hasn't helped.

I have also googled this and it seems to be a known error but none of the solutions helped (or these involved writing shell-scripts which seems a bit over-complicated).

It must be just an issue of changing a setting somewhere and I am hoping that someone can point me towards the correct place?

Many thanks,
Alan Searle

---

### Post by asearle on 2008-11-29
I have been trying to fix this problem and so, in System Settings, I experimented with File Associations and seemed to have caused a problem:

Now, when I boot the system I repeatedly get the message "Sorry / KDE Panel ... Could not find mime type application/octet/stream".

Is there any way I can reset the file associations to their default?

Here I am assuming that they don't have anything to do with my 'links unavailable from thunderbird' problem?

In Default Applications, I have set FireFox as the Web browser but that also didn't get the links working.

Many thanks for any tips that you have.

Cheers,
Alan Searle

---

### Post by poliltimmy on 2008-12-07
I have done every step mentioned still no luck. tbird will not launch firefox2. I have tried to completely remove and fresh installs. After an hour of uninstalling and trying each solution on a fresh install. I have tried the launchpad fix to no avail. I must come to the conclusion that Ubuntu does not take this seriously. And neither does Mozilla. After all the problem has been around for a good while now.

Ubuntu 8.04.1 AMD 64
Firefox 2 (out of the repos)
Tbird (out of repos)

  Since all come from Ubuntu repros, why they will not work together baffles me. Could have removing Evolution and Firefox3 from my system caused this?

---

### Post by xebian on 2008-12-07
It's for security reason why the default is not to open the link.  It could be a scam/fraudelent site.

---

### Post by poliltimmy on 2008-12-07
> **xebian said:**
> It's for security reason why the default is not to open the link.  It could be a scam/fraudelent site.

Every site? I'm sure my Vonage account email links should work. I have checked all http links in emails none open.

---

### Post by poliltimmy on 2008-12-07
The Thuderbrowse extension will work, kind of. It's a bit awkward but the links will open inside Tbird . The right click: Visit in Browser does not work on my machine. The other options are working fine. And fast too. I guess I can live with it. Since I should have posted in another thread thanks for your patience.

---

### Post by a_px on 2009-01-30
I just discovered how to fix this:

[http://ubuntuforums.org/showthread.php?t=51206&highlight=thunderbird+web+links]("http://ubuntuforums.org/showthread.php?t=51206&highlight=thunderbird+web+links")

Alan

---


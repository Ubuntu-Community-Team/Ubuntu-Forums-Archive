---
title: "Sharing thunderbird in different OS's"
date: 2009-04-13
forum: General Help
---

### Post by shawnjones on 2009-04-13
Hello all,

I have been a long time user of Ubuntu and linux in general. I have recently taken a job that requires me to use Windows XP. I use gmail for my mail and I can access and use my gmail, through Thunderbird, from both OS's. The problem is that if I open TB in Ubuntu it downloads my new messages, that's fine. But if I use TB in XP it doesn't show the messages that were downloaded from TB in Ubuntu. This works vice versa. This makes using my email quite hard because some messages are in XP and some in Ubuntu.

Is there a cure for this mess, or do I just need to quit my job because I despise Windows?

Thanks in advance,
Shawn

---

### Post by wilbbe01 on 2009-04-13
You are probably using pop.  If you set Thunderbird in both OSes to use IMAP in the server settings instead of POP your problem will go away.  IMAP stores messages on the server, so things are the same everywhere no matter what you have opened.  You can look at instructions via the settings in gmail.

---

### Post by shawnjones on 2009-04-13
I am already using IMAP, I should have mentioned that. Sorry.

Thanks for the tip though.

---

### Post by crossedout on 2009-04-14
I don't know if its an option for you but if you setup a fat32 partition and place your TB info there it will work.  Just have both OS point to the fat partition and whenever you download new mail it will store there, thus all email can be read from either OS and organized together as well.

I used to use that method for a while until I no longer needed XP syncing.

-Xout

---

### Post by ninjapirate89 on 2009-04-14
In thunderbird click on Edit -> Account Settings and find where it says server settings. Under this there is an option to leave messages on the server.

---

### Post by rage9 on 2009-04-14
If your using the same computer with both XP and Ubuntu on it.

[LIST=1]
[*]Ceate a small NTFS partition.  I call this the Mutual Zone.
[*]Adjust your /etc/fstab file to automatically mount it.  Windows will automatically recognize it.
[*]Refer to [this article]("http://www.mozilla.org/support/thunderbird/profile") to find your profile.
[*]Move your profile to the Mutual Zone.
[*]Edit your profiles.ini file on each OS to point to the profile in the Mutual Zone.
[*]...
[*]Profit!
[/LIST]

---


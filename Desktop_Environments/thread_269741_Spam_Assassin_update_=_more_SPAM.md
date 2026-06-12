---
title: "Spam Assassin update = more SPAM"
date: 2006-10-02
forum: Desktop Environments
---

### Post by ngms27 on 2006-10-02
Hi,

I updated Spamassassin last week and since then my Spam has come back. Any ideas how I can make this work again with Evolution?

This was the Ubuntu update BTW

---

### Post by lobstaj on 2006-10-06
Hello,

I have the same problem. Dapper update, I think now it's spamassassin 3.1.3. Since I upgraded, I think it doesn't filter any spam at all.

I have already checked that spamassassin is running, and when I press the 'Spam' button in evolution, I see that there is the spamd process. Also, it updates (i.e. accesses) the files in ~/.spamassassin ...

After I tried everything that came to my mind, I am quite fed up with evolution. There should be some feedback about whether everything is done from the user's side in order to filter spam.
Before I got it to work, I was also fighting for some time. (because it does not tell you any errors - even if spamassassin is not installed at all... or anything else is wrong)

I'm a switch to KDE soon.. ](*,)

PS: The bogofilter plugin is disabled, yes! And the spamassassin plugin is enabled...

---

### Post by NRios on 2006-10-09
I am also sick and tired of Evolution. I have given it a full year trial, hoping that it would get better, but I'm thinking of dropping it for good. I'm tired of waiting 20 minutes for all the spam to download, then spending more time to manually delete it. I'm tired of *S*L*O*W* operation and frequent freezes. Evolution is really not ready for the desktop.

It is a pity, because I like the concept of Evo's address book and calendar data being available to the Gnome desktop, but it should work right before that was an advantage. But I'm moving to Thunderbird NOW, and bugger the integrated calendar; I never use it anyway.

---

### Post by lobstaj on 2006-10-09
> **NRios said:**
> ... and bugger the integrated calendar; I never use it anyway.

But I do use the calendar... :(

---

### Post by NRios on 2006-10-09
There is a project for an independent calendar and addressbok that uses Evolution Data Server ("Dates" and "Contacts" by Opened Hand. It seems to be at a very early stage, but is even an Ubuntu deb repository. See o-hand.com.

---

### Post by tcarradine on 2006-10-23
hey guys- felt I needed to post this since no one else had in so many words!

for those of us who do need/want to use Evolution the simple work around for this problem is to remove SA 3.1.3 and roll back to the previous version (in this case 3.1.0a). That way you can at least continue to have your junk mail filtered until the devs fix whatever bug is causing the break in functionality. 

Thanks to lobstaj for making the connection and getting me out of a 50-to-100-spam-per-day-jam!

Tim

---

### Post by the-linux-guy on 2006-10-24
> **tcarradine said:**
> for those of us who do need/want to use Evolution the simple work around for this problem is to remove SA 3.1.3 and roll back to the previous version (in this case 3.1.0a).

Or you could *upgrade* to version 3.1.5, downloaded from spamassassins website and install it manually according to the manufacturer instructions... Works for me, even with evolution...

---


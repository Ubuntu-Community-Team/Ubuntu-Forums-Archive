---
title: "The possibility of a better email client ??"
date: 2008-11-02
forum: Desktop Environments
---

### Post by oygle on 2008-11-02
Evolution, Kmail, Thunderbird and Claws, I have tried them all, and none of them have the features of Pegasus Mail. It appears that there _may_ be a possibility of a Linux version of Pegasus Mail, mentioned in [this thread]("http://community.pmail.com/forums/1/8987/ShowThread.aspx") recently ..

> As for a native Linux version that's much more of a problem.  Writing a program that is OS neutral requires using a totally different approach than writing a Windows program.  You can do this with PHP, Java and/or another high level language where there is a run time complier available on the OS but this really slows things down.  Maintaining two separate versions of the program is also not an option where there is only david involved in the programming.  This was the basic reason the the Mac version went away a long time ago.

However, it appears that there we no takers for the Linux version of Pegasus

> David has offered up support to the Linux community to for someone to develop the Linux version but there were no takers.

I don't know who David contacted, but it would be a **HUGE** bonus for Linux (Ubuntu ? ) users, if Pegasus Mail was available, as an email client.

Please contact [David Harris]("http://pmail.com/contacts.htm") if you are interested.

---

### Post by pansz on 2008-11-03
If you really interested in Pegasus mail, would you please just describle the unique features of Pegasus mail?

---

### Post by DirtDawg on 2008-11-03
According to the [Wine App Database entry]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=6462&iTestingId=25204"), Pegasus runs well under Hardy(7.04), but may not under Ibex(7.10). If you haven't already, give Wine a try.

---

### Post by oygle on 2008-11-03
> **pansz said:**
> If you really interested in Pegasus mail, would you please just describle the unique features of Pegasus mail?

Please see the [Windows overview documentation]("http://www.pmail.com/overviews/ovw_winpmail.htm")

---

### Post by oygle on 2008-11-03
> **DirtDawg said:**
> According to the [Wine App Database entry]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=6462&iTestingId=25204"), Pegasus runs well under Hardy(7.04), but may not under Ibex(7.10). If you haven't already, give Wine a try.

That comment on the WINE apps page is made by one person, and isn't correct. Scroll down and see 2 reported bugs, plus the other problems with running Pegasus under WINE.

I have been using it under WINE for some months now; it does have problems under WINE. Seems if an app isn't a 'game', then the WINE developers aren't that interested ??

That's why I posted about the possibility of a native/Linux Pegasus Mail.

---

### Post by DirtDawg on 2008-11-03
> **oygle said:**
> That comment on the WINE apps page is made by one person, and isn't correct. Scroll down and see 2 reported bugs, plus the other problems with running Pegasus under WINE.

I have been using it under WINE for some months now; it does have problems under WINE. Seems if an app isn't a 'game', then the WINE developers aren't that interested ??

That's why I posted about the possibility of a native/Linux Pegasus Mail.

Too bad. Hopefully coders will be more inclined to design projects platform independent from the beginning as Linux grows in popularity.

---

### Post by oygle on 2008-11-10
Have received the following recommendation from a KMyMoney developer .

>  I would recommend using Qt as a library to maintain compatibility across platforms, no doubt.  And since the program is written in C (maybe C++) it could be feasible.

---

### Post by ciscosurfer on 2008-11-10
@OP,

What features are *you* specifically looking for?  In other words, what features are lacking in the current clients that you miss?  I read the laundry list on the page you provided.  You could always put in a feature request to one of the previously mentioned clients that are already supported under Linux and Ubuntu...

---

### Post by oygle on 2008-11-10
> **ciscosurfer said:**
> @OP,

What features are *you* specifically looking for?  In other words, what features are lacking in the current clients that you miss?  I read the laundry list on the page you provided.  You could always put in a feature request to one of the previously mentioned clients that are already supported under Linux and Ubuntu...

These are just some that spring to mind in Pegasus ..

1.  The ability to have seperate 'users', that is, you can completely seperate entire sets of email boxes, by user name. You login by user name. This is very helpful where you may want to completely seperate entire sets on emails.

2.  Within each 'user', you can have many 'identities', that is, you can setup the identity as an account profile. This sort of feature is in most email clients, some call it an account. Pegasus have many options to be used within identities.

3. Searching within the entire email box, or individual folders, for any string, search results are simply stored as a link to the emails.

4. Very comprehensive WYSIWYG for sending emails, send text, html, rtf, etc, etc.  Attach anything you like with whatever encoding you specify.

5.  Flags to indictae on every email, if it has been replied to, fowarded, etc, etc.

6. No doubt many other features that I have just come to take for granted, but notice them missing in other email clients.

Good point about contacting developer/s for some of the other email clients. I'd say, at a guess, even though my Kmail useage has been limited, it is the 'closest' email client to pegasus (especially the manner in which emails and email storage folders/boxes is arranged.

Thanks,

Oygle

---

### Post by irrdev on 2008-11-10
> **oygle said:**
> These are just some that spring to mind in Pegasus ..

1.  The ability to have seperate 'users', that is, you can completely seperate entire sets of email boxes, by user name. You login by user name. This is very helpful where you may want to completely seperate entire sets on emails.

2.  Within each 'user', you can have many 'identities', that is, you can setup the identity as an account profile. This sort of feature is in most email clients, some call it an account. Pegasus have many options to be used within identities.

3. Searching within the entire email box, or individual folders, for any string, search results are simply stored as a link to the emails.

4. Very comprehensive WYSIWYG for sending emails, send text, html, rtf, etc, etc.  Attach anything you like with whatever encoding you specify.

5.  Flags to indictae on every email, if it has been replied to, fowarded, etc, etc.

6. No doubt many other features that I have just come to take for granted, but notice them missing in other email clients.

Good point about contacting developer/s for some of the other email clients. I'd say, at a guess, even though my Kmail useage has been limited, it is the 'closest' email client to pegasus (especially the manner in which emails and email storage folders/boxes is arranged.

Thanks,

Oygle

I'll respond to some of your points. I have not used Kmail, so cannot comment on that email client, but I am fairly familiar with Thunderbird, and particularly Evolution.

1. Thunderbird allows you to do this. You can enable the profile manager to begin at startup, from which you can setup and load different profiles/users. 

3. Both Thunderbird and Evolution include integrated "filter" search abilities. You can search the current folder, folders, or message. The emails which include the search phrase are listed in the message pane.

4. Both Thunderbird and Evolution fully support WYSIWYG email editing/creation. You can format your email in either plain text or html. Attachment types are automatically detected by their extensions. I believe Thunderbird may allow you to choose the encoding, but I am not positive.

5. Both Thunderbird and Evolution include automatic and manual flagging capabilities. The implementations may be slightly different, but they essentially perform the same task by changing the icons and colors.

---

### Post by lisati on 2008-11-10
> **pansz said:**
> If you really interested in Pegasus mail, would you please just describle the unique features of Pegasus mail?

You can automatically update mailing lists by the use of rules/filters, customizable junk mail controls,.....just to name two features.

---

### Post by oygle on 2008-11-10
One of the problems, as I see it, with Thunderbird and Evolution, is that the email boxes are one (huge) file, which can significantly increase the chances of data corruption in the event of a system hang, etc.

Pegasus on the other hand, is like Kmail, which stores each folder as a seperate file, and each file has it's own index file. Every new mail msg is also a seperate file, and attachments can be deleted , if need be (great after an attached pic is saved to disk, ... why keep it in the email, just delete it).

The file control issue is important for me, as I have over 700Mb in total (email folders and boxes), so you can imagine if Thunderbird or Evolution were continually writing to a file that large.

---

### Post by moron on 2008-12-29
So far every feature you have listed is offered by Kmail except perhaps the concept of choosing a distinct user upon startup (it definitely does have identities though just not sure about a Mozilla style user profile as I have no personal need for that).

Are you sure that this is not just a case of being familiar with Pegasus' GUI as opposed to other programs not offering the features you want?

Cheers

---

### Post by oygle on 2008-12-29
The features of Pegasus I listed were only a very brief and cut down version of all the features.

Having used Pegasus for about 15 years, and using KMail now for 3 months or more, I can assure you that KMail does not have any where near all the features that Pegasus has.

Still, Pegasus can only be run under WINE in Ubuntu, and as there are a few minor annoyances with it under WINE (like exiting when you send an email), and the WINE developers don't seem interested to fix the problems, I decided to go with KMail anyway. It was the 'closest' email client to Pegasus , has an import function for Pegasus mail boxes, and has all the 'basic' features I need. I'll just to have to forget about all those extra nice features.  :D

Oygle

---

### Post by freacert on 2009-05-07
Just starting today, importing my pegasus mail into Kmail. (over 10 years of mail)

I note that the annotations which i made in pegasus are gone. Noting that Kmail will not let me choose a folder to store the sent message in. 

Love to see pegasus in ubuntu.

---

### Post by albinootje on 2009-05-07
> **oygle said:**
> Evolution, Kmail, Thunderbird and Claws, I have tried them all, and none of them have the features of Pegasus Mail.

As a system administrator who has dealt with Pegasus Mail to Sylpheed and Thunderbird migrations I can tell you that imho Pegasus Mail is a huge pain to work with, stay far from it if you can.

I can imagine that you've used it for years and you think it is good, and you have a hard time to move away from it, but this is my point of view from my experience.

And concerning importance for Linux (Ubuntu) and email clients, I think that Evolution and projects like OpenXchange are making good progress. 
And Mozilla Lightning and Sunbird are getting close to version 1.0 which is good for everyone.

---

### Post by oygle on 2009-05-08
> **freacert said:**
> 
I note that the annotations which i made in pegasus are gone.


If there is something similiar in KMail (annotations), then you will notice after importing, you still have the Pmail header/s there, so it would be possible, with some code to find the matching message in KMail and add the annotation. I'm not sure if KMail has something like annotations though.

> **freacert said:**
> 
Noting that Kmail will not let me choose a folder to store the sent message in. 


KMail has 'identities', just go to 'config KMail', modify that identity, and then the third TAB is the 'advanced' tab, and yu can set the 'sent' folder there.

I made the 'move' to KMail, Thunderbird, Evolution and others are nothing like Pegasus mail, but KMail was the 'closest', so I'd advise anyone moving from Pegasus, to use KMail. The KMail mailing list has good support.

HTH

Oygle

---

### Post by mister_p_1998 on 2009-05-08
> **oygle said:**
> These are just some that spring to mind in Pegasus ..

1.  The ability to have seperate 'users', that is, you can completely seperate entire sets of email boxes, by user name. You login by user name. This is very helpful where you may want to completely seperate entire sets on emails.

you can do this in Thunderbird, either by separate ubuntu logins, or by mail filtering which moves email to : john@aol to one folder and Kim@bt to another, I do this for my wifes computer using several emails & Yahoo groups & Gmail accounts.


2.  Within each 'user', you can have many 'identities', that is, you can setup the identity as an account profile. This sort of feature is in most email clients, some call it an account. Pegasus have many options to be used within identities.

Thunderbird does this also..



Oygle

Steve

---


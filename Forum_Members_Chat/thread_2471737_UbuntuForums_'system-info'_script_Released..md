---
title: "UbuntuForums 'system-info' script Released."
date: 2022-02-08
forum: Forum Members Chat
---

### Post by MAFoElffen on 2022-02-08
Back in August, I started a thread here (Inspired) about an Ubuntu Support Script that I dedicated to the Forum Users here-- to help Forums Users to be able to help Users needing help. It creates a report on the User's hardware, system and settings, so that people trying to help them have a better idea on what they are recommending solutions for. That was received very well by Members in this section here.

The thread was moved from here to "Programming Talk"... [https://ubuntuforums.org/showthread.php?t=2465764](https://ubuntuforums.org/showthread.php?t=2465764)

It has since been completed, thoroughly tested, accepted and endorsed by the Forum Admin Council, and is available from the UbuntuForums GitHub.

That is the background and update... Reviews by Forum Users has been good and it has been very useful in diagnosing and helping to solve problems... I am continuing to find ways to improve it.

Now? In the past, something like this would have been announced or information about it put into a Sticky. I was told that now-a-days people do not read or pay attention to Sticky's. That the most appropriate place for a Sticky on this, if there was, would be the Hardware Section, but that there was many Sticky's there already. Announcement in a Post? I don't know where would be appropriate or noticed.

What I was told to tell the group o testers, was to just tell Users, and to put a link to it in our signature lines...

So I am posting here, where I know there are "Ubuntu Members" that I know help people on this Forum. Here is a useful tool or you to use... Many of you have been active in it's testing, and that help was invaluable. Thank you.

Does anyone have any ideas on how to get the word out on it?

---

### Post by Paddy Landau on 2022-02-09
This is interesting. Thank you for creating this!

Didn't there used to be a script very similar to this? But, as I recall, it didn't provide a preview, and it uploaded automatically to pastebin.

I've just tested this on Lubuntu (in VirtualBox), and it seemed to all go well. I didn't use the pastebin option, though.

I have a couple of small suggestions about the script.

**User input**

For your [FONT=courier new]read[/FONT] commands in function [FONT=courier new]UserInput[/FONT], might I suggest that you use the options [FONT=courier new]-e[/FONT] and [FONT=courier new]-r[/FONT]?

So, instead of:
```
read -p
```
use
```
read -erp
```

[LIST]
[*]Option [FONT=courier new]-e[/FONT] makes the input more intuitive to the user, e.g. when using the back-arrow. I tried to use the back-arrow to correct a mistake, and got nonsense instead &#128522;
[*]Option [FONT=courier new]-r[/FONT] prevents the backspace, if entered by the user, from being seen as an escape character. So, if the user finds the backspace important, it will be retained.
[/LIST]

**Spelling mistake**

On lines 945 and 949, *publically* should be *publicly*.

I think it that your script works well. I wonder if it might be of use to also advertise this to Reddit on [/r/linux4noobs]("https://www.reddit.com/r/linux4noobs/") and [/r/linux]("https://www.reddit.com/r/linux/")?

---

### Post by MAFoElffen on 2022-02-09
@Paddy Landau

Thank you for catching the spelling errors, and the other suggestions. 

I welcome any input if someone catches something or thinks it might need an improvement. Many if the things there, are questions we have asked User's time and time again, while trying to help them... We did try to sanitize information pasted to a pastebin or post-able, so that it protects our Users.

I just got home from a closing shift. I will look at those in the morning and push some changes to the Repo's.

I honestly never thought about Reddit, but I very rarely ever go there. Because of that, I didn't know those areas existed there. Which gives me an idea that I could probably post something on LinkedIn in the Ubuntu Groups, and the Linux Sys Admin Groups I belong to there.

EDIT: Made those changes. Will Push those later... I have two corrections / improvements I want to add and push with them...
EDIT2: Pushed the changes and enhancements to DEV and STABLE...

---

### Post by MAFoElffen on 2022-02-09
Update...

So far I announced it on the 2 REDDIT Groups that Paddy Landau suggested. 
EDIT: It was refused until I build enough 'Karma' there to know I am safe. Had to do the same at Ubuntu Discourse. 

I also announced it on LinkedIn to my Network and the Groups: Ubuntu Users Official, Ubuntu Expert, Ubuntu Administrators, Ubuntu, Linux Opensource Communications Platform, System Administrator...

I still think we should announce it here 'somehow' and 'somewhere'... Doesn't it just seem a bit odd that I am announcing it outside of the Forum, for use here, by our own Users? That is what I thought when someone suggested announcing it at Ubuntu Discourse, just for our own Ubuntu Weekly Newsletter to possibly scrape from.

---

### Post by Paddy Landau on 2022-02-10
> **MAFoElffen said:**
> I still think we should announce it here 'somehow' and 'somewhere'...
Agreed.

Further suggestions&#8230;

[LIST]
[*]Announce this on [New to Ubuntu]("https://ubuntuforums.org/forumdisplay.php?f=326"), and ask for it to be stickied. Or, maybe better, ask for it to be included in the existing sticky [Suggestions on how to get your support questions answered as quickly as possible]("https://ubuntuforums.org/showthread.php?t=1422475"), inside the *Hardware Information* section.
[/LIST]

[LIST]
[*]Don't wait for the Ubuntu Weekly Newsletter to "scrape" the idea. Instead, contact them directly and let them know.
[/LIST]

[LIST]
[*]Write a short article for [Full Circle Magazine]("https://fullcirclemagazine.org/") explaining what what the script is, when and why to use it, and (especially for newbies) how to use it. FCM, which is read by many users of Ubuntu & derivatives, is desperate for new articles. Send the article to Ronnie, email *ronnie *at* fullcirclemagazine *dot* org*. If you're unfamiliar with FCM, read the [latest edition]("https://fullcirclemagazine.org/issue-177/") or see the [archives]("https://fullcirclemagazine.org/downloads/").
[/LIST]
Most important, I think, is to ensure that the explanation of how to use it is clear to newbies. Perhaps find a couple of newbies on [/r/linux4noobs]("https://www.reddit.com/r/linux4noobs/"), ask them to follow your instructions, and have them feedback to you how well it went. It's easy for people like you and me to forget how difficult it is for a newcomer to understand!

---

### Post by MAFoElffen on 2022-02-19
Update:

Reddit approved both posts there. I posted in multiple areas on LinkedIn.

It  got picked up from somewhere as a Headline on the main page of  DistroWatch Weekly 955, titled "Ubuntu gets new tool to gather system  information.": [https://distrowatch.com/weekly.php?issue=20220214](https://distrowatch.com/weekly.php?issue=20220214) It  recieved a great review, where it also recommended it for all Main  Distributions, including Fedora...

I've been working with the  Admin's, and helped them edit/update the "Suggestions to get your support  questions answered as quickly as possible" Sticky in the New Users  Section, where we included information and links to both the 'system-info script, and separately, to the 'wireless-info' script Sticky. That Admin (coffeecat) is working with me to add a sticky to  that section and the Hardware section on the 'systems-info' script.  After those Stickies are there, then I will post in those sections to  announce it.

---

### Post by Paddy Landau on 2022-02-20
That's excellent work, MAFoElffen!

Here's the [Distrowatch article]("https://distrowatch.com/dwres.php?resource=showheadline&story=14292") for reference.

---


---
title: "Setting up CUPS, ......&quot;Enter user name and password????&quot;"
date: 2006-09-29
forum: Desktop Environments
---

### Post by alanmzifa on 2006-09-29
Hi, trying to move the migration to Linux another increment further.

This week's problem, trying to add a printer. Well, printer is added but the options the print GUI gives me are so basic as to be useless so I've discovered that there are other drivers that provide more print options here and as I have an HP printer I'm told  need HPLIP which appears to come with the basic Ubuntu distribution. 

In activating it through CUPS web browser interface I'm presented with a screen tab called "installation" where I can add the printer.

Unfortunately when I click add printer I get a pop up dialogue box that says "Enter username and password for CUPS at http://localhost:631" .

The only password and user name I'm aware of is the laptop's login details but they don't work.

Can someone please point me in the right direction here and tell me where I'm going wrong.

thanks

---

### Post by brucevangeorge on 2006-09-29
You need to search for user name and password for cups.

Its been discussed in great detail before... use the search box. Shouldn't take more than a couple of minutes to find.

---

### Post by danderson3 on 2006-09-29
you can use root and its password

David

---

### Post by alanmzifa on 2006-09-29
thanks.

I found [this]("http://ubuntuforums.org/showthread.php?t=263180&highlight=user+password+cups") and [this]("http://www.kdedevelopers.org/node/2117/"). Tried the first and got the same error one of the posters got about a "child error 15" so then did what was mentioned in the the second link.

Seems to have installed the printer but not in a way that makes any difference when I go to print something.

If I go into HPLIP toolbox I can change some things like collate and print from last page which is a start. However I can't seem to get to that screen from the standard print command in the browser for example. I just get the previous standard bare-bones useless print GUI dialogue pop-up.

What's the secret? How do I get the "proper" [properties box]("http://hplip.sourceforge.net/screenshots.html") up when I want to print something?

thanks

I'll try to post a pic to show what I mean.

---

### Post by alanmzifa on 2006-09-30
polite bump

---

### Post by brucevangeorge on 2006-10-01
So I'm guessing installing through the web interface worked?

Another thing to take into account is that most of the gui interfaces don't work too well. Didn't work for me.

Whenever I want to change printer setting I have to go through cups WEB.

---

### Post by alanmzifa on 2006-10-02
Yes, I installed the web interface but I can't say it gave me the options I wanted. I was expecting to get the ability to print various qualities and collate documents, more than 1 page per sheet, start printing from last page etc. and all via a GUI. 

Am I being stupid or is this just not available within Linux in a GUI?

---

### Post by sumgai777 on 2006-10-05
Gee, BruceVanGeorge, 

really, really helpful - NOT.

You obviously know the answer to the question.
You chose to spend the 30 seconds to post.
But your answer was "hey - search more" - instead of (for the same effort) "here's what to do".

I moved from Gentoo to Ubuntu 2 months ago due to arrogant, flip attitudes from the forums in response to user problems like this (which aren't immediately intuitively obvious as to how to solve).

Be part of the solution, my friend - not part of the problem. It wouldn't have taken you any more time to help out that guy - vs. telling him "it's been answered before".

Be nice. It don't cost nothin'.

Sumgai

---

### Post by BitTwiddler on 2006-10-09
Hi,

I had the sample problem. All I needed to do was to assign a password to the root account and I was able to login as root with SWAT.

Hope this helps

---

### Post by traglet on 2007-11-20
The problem is probably that you're not a member of the lpadmin group.  Try this:

sudo usermod -a -G lpadmin ${USER}

Then you should be able to use your own username & password to administer CUPs.

---


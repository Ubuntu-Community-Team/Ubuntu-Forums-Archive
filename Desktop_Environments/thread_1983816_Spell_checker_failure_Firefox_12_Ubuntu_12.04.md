---
title: "Spell checker failure Firefox 12 Ubuntu 12.04"
date: 2012-05-20
forum: Desktop Environments
---

### Post by steveparbkk on 2012-05-20
This is hugely irritating.  I typically use British English.  Occassionally I use Thai too.  I hadn't used Thai for a while, since upgrading to 12.04.  When I wanted to use Thai fonts recently, I noticed that since upgrading to 12.04, Thai was no longer an installed language so I moved it up the list in Lanuage support settings.  All seemed fine until I wanted to use Firefox.  When I started to type a message in Firefox, in English,  noticed that ALL my words were marked as incorrectly spelt (even my spelling isn't that bad!).  When I right click in the text box and look under lanuages (using Firefox) I note that it states that Thai/Thailand is selected.  There are several versions of English to choose from otherwise just Thai and Thai/Thailand.  If I choose Thai the black dot which indicates which language is selected disappears (And I note that the words I type are no longer marked as incorrectly spelt, eeven if they are incorrectly spelt!).  If I choose any other language choice (all of which are various versions of English with the exception of Thai/Thailand) the black dot indicator appears next to Thai/Thailand.

As you might imagine, I decided to deselect Thai under language support, but it doesn't make any difference.  So, the net effect of all of this is that my spell checker in Firefox is completely useless.  Do you know how much we come to depend on spell checkers??  Believe me, you don't want to know.

Addionally, I should add that under about:config in Firefox, the spellchecker.dictionary string indicates th_TH.  I can change it back to en_GB, and it appears to work, until I try to type something when it appears to revert to th_TH.  Of course, I'm assuming this is an Ubuntu issue rather than a Firefox issue as it arose only after I added Thai lanuage support in Ubuntu.

One further development.  I decided to uninstall the Thai language package too, to see if that would resolve the spell checker problem and it has (except I now don't have Thai language any more).  After the installation and upon going back into Language support I saw the message something to the effect of : 'Your Language packages are not properly installed.  Would you like to fix this now?' [I'm not sure exactly what it said but something like the foregoing]  I said yes and then I received the following message 'Failed to fetch [http://th.archive.ubuntu.com/ubuntu/pool/main/p/poppler-data/poppler-data_0.4.5-2_all.deb](http://th.archive.ubuntu.com/ubuntu/pool/main/p/poppler-data/poppler-data_0.4.5-2_all.deb) Something wicked happened resolving 'th.archive.ubuntu.com:http' (-5 - No address associated with hostname)'  I then did an nslookup and got the following results:

nslookup th.archive.ubuntu.com
;; connection timed out; no servers could be reached

XXXXX@XXXXXXXXXX:~$ nslookup th.archive.ubuntu.com
Server:		127.0.0.1
Address:	127.0.0.1#53

** server can't find th.archive.ubuntu.com: SERVFAIL

Whereas a control lookup produces:

nslookup [www.ubuntuforums.org](www.ubuntuforums.org)
Server:		127.0.0.1
Address:	127.0.0.1#53

Non-authoritative answer:
Name:	[www.ubuntuforums.org](www.ubuntuforums.org)
Address: 91.189.94.12

If ANYONE has any suggestions as to how I might resolve this nightmare, please let me know.  This is now much less a nightmare than it was, although needless to say I now no longer have Thai language support.

Well, there have been some updates recently.  I decided to see if they had resolved my issue.  I have just re-installed Thai fonts and the spell checker issue has now been resolved.  So, it would appear as though I have my Thai fonts and can still have my en-GB spell checker!

---

### Post by L a r r y on 2012-05-26
I discover that I have no spell checker in Firefox 12 on Ubuntu 12.04, with system settings being set for United States English.

Spell check is enabled in Firefox on the Advanced, General tab in Preferences.  And it is aa pain in the neck because the USB keyboard I am using drops spacebar keypresses, leaving me with words run together.

I remember seeing everything misspelled on the Firefox 12 in Ubuntu 10.04, so maybe this is a Firefox issue instead.  Maybe an Ubuntu Firefox issue.

I don't recall what I did over there, maybe I turned off the spell checker.I don't have a USB keyboard on that computer because it was not at all very kind to me -- maybe I got a bum keyboard!  

We recently had an Ubuntu presentation at our local radio club meeting, and I shall bring this spell checker issue up with the presenters in the next meeting in June.

---

### Post by overcast on 2012-05-26
I don't think this issue is of desktop environment. More like applications issue, so should be in respective category. That said,I have few plugins disabled by default in firefox, so I too am looking for the answer.

---

### Post by L a r r y on 2012-05-28
Just for what it's worth, I'm on my 10.04 computer and spell check is working fine.  TeSt -- It underlined the mis-cased word.

I am not using Flash over here, that will cause this computer to just come to a crawl after a short while.

I am using Flash over there on the faster computer, and it displays videos for the first time ever on a Linux box for me in real time.  It does bog down if I run a playlist in full screen on YouTube.

On both computers, instead of using the BetterPrivacy add-on for Flash cookies, I have instead made the LSO directory under .macromedia read-only.

I use AdBlock Plus, and use Cookie Monster on both machines, telling Firefox to accept all cookies, but dump them when I close Firefox, and then override that setting on a per-site basis to accept and keep cookies where I have to log in and where I can set preferences.

Here I have Enter Selects 7, More Tools Menu and Menu editor, together with DownloadHelper 4.9.9.  The latter has the three balls icon, and in 12.04 it is called Video DownloadHelper, which has the same three balls.

Over on my 12.04 I have not added the More Tools Menu, Menu Editor or Enter Selects yet.

Over here on 10.04 I have the profile switcher left over from older versions of Firefox.  my understanding is that the profile switcher, whatever it is officially called, is no longer offered.

Now, I did open up a no-add-ons profile here and had no spell checker.  So I wonder if it has anything to do with your profile?

I had to open up a clean profile to be able to upload larger images to my wiki web site.  I have it set with Cookie Monster and AdBlock Plus at least, with the same cookie settings in Firefox to keep all cookies until I close Firefox.

I will close and bring up that profile and see if it does spell check.....

---

### Post by L a r r y on 2012-05-28
Ubuntu 10.04, Firefox 12, even with NO add-ons found the spell checker working.  I misspelled a word in the Google search box once and it was marked as misspelled, but in another profile I tried the same search and it did not mark, so I brought up the Wikipedia sandbox, and there I got misspelling marked.

Apparently related to 12.04 Ubuntu and Firefox 12.

---

### Post by pqwoerituytrueiwoq on 2012-05-28
make sure a dictionary is checked

---

### Post by L a r r y on 2012-05-30
> **pqwoerituytrueiwoq said:**
> make sure a dictionary is checked

Where do I look for a dictionary check box?  In Firefox?  In Ubuntu?



I do have an update to report on:  I submitted a support ticket pertaining to something else, and in their edit window I had an active spell checker.  I closed out the many tabs I had opened a day or so ago and opened anew Firefox session.  I come in here and participate in a number of threads, and there is NO spell checker active on the ubuntu forum edit windows.

I was about to say the issue seems to have righted itself before I came in here and found the same old problem still hanging around!  I'll go start another support ticket and misspell a few things and see what happens.....

New tab,  leave this edit open and I open a new support ticket in another tab.  I write:

missspellled and the word is underlined.

I return to this tab and start writing with the words, "New tab," and write that misspelled word, and the spell checker is working.

What gives!  It also worked on the misspelled amd for and.  And right click on the misspelled word  to get the dictionary's suggestions, just as it should.

My solution, I go over to my web site support center and start a new ticket, misspelling something, then return to the tab I am working in????

Apparently I don't have American English dictionary either, because I have to spell it as "centre" to avoid being red-lined.

One thing I noticed about Ubuntu 12.04, the date format is 25 May 2012, and nowhere is there the American May 25, 2012 option available, if that is at all related.  Because I am using US English in my Ubuntu setup!

---

### Post by L a r r y on 2012-06-07
**I may have an answer for the Firefox spell check issue.**

Reading in the Mozilla Knowledgebase, I was able to make a setting in about:config that gets the spell checker going from the start.

With Edit >> Ppreferences, in the Advanced tab's General tab, you have to have the "Check My Spelling as I type" activated with a checkbox ticked.

Begin with the address in the location bar:  **about:config**
You have to "promise to be careful" to get into the configuration editor.

Quoting from the Mozilla knowledgebase article [http://kb.mozillazine.org/Spell_checking](http://kb.mozillazine.org/Spell_checking):
> 
    Set the **layout.spellcheckDefault** preference to 2 (default = 1)
    Set the **spellchecker.dictionary** preference to your locale (e.g., to en-US for US English)
    Restart Firefox if you made any setting changes and then test spell checking. 



You can enter the bold phrases into the search box and that will display the needed preference.  Right-click on the preference and select "Modify" and set the layout.spellcheckDefault to a value of 2.

It is this value that makes it activate spell checking for me,

I also checked the dictionary, which by default is US English, but was user set to en-GB.  I set it to default en-US.

Restart Firefox for changes to take effect:  I rebooted the computer just to be sure I was starting from scratch, and the spell checker works right off in multi-line input boxes.

I still have the issue of the wrong dictionary because it rejects "color" in favor of "colour" and "center" in favor of "centre."  But I checked about:config and it is still set for en-US, the default.  That may be an Ubuntu issue.  I do not have the American date format available or American English available.

Hope this helps out!

---

### Post by L a r r y on 2012-06-20
Sad to say, my spell checker is as unreliable after my last posted "solution" on Ubuntu 12.04 as ever.  It works seemingly in the second tab opening.  I did not look to see if my changes were reverted, but if they were, then the solution I proposed is of no value in the long term.  I thought surely it was fixed when I booted from scratch and had a spell checker working right after my about:config change.

I am sorry I did not have a working solution for the o.p. of this thread.

---

### Post by stankan on 2012-11-20
There is a simple fix I found in another forum for this.  If you right click in the middle of a text box you will get a menu.  Click on languages then an available language.  It worked like a charm for me.

Stan

---

### Post by L a r r y on 2012-11-21
> **stankan said:**
> There is a simple fix I found in another forum for this.  If you right click in the middle of a text box you will get a menu.  Click on languages then an available language.  It worked like a charm for me.

Stan

Sure enough I am using Australian English over here.  I moved that to United States English.

Thanks Stan!

Seeing proper spellings for my version of English accepted as proper, with British spellings called out as  "wrong."

Now I will have to switch to other versions of English and see what works and what doesn't.

---


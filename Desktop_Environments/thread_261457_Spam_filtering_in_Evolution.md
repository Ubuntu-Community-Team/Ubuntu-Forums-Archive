---
title: "Spam filtering in Evolution"
date: 2006-09-20
forum: Desktop Environments
---

### Post by Garyu on 2006-09-20
I have enabled the spam filter in Evolution, and I keep sending spam to the junk folder, but nothing is ever filter out...

I found this thread:
[http://ubuntuforums.org/showthread.php?t=99603](http://ubuntuforums.org/showthread.php?t=99603)
which deals with spam filtering using "bogo" and "spamassassin", but I thought this would be a built-in feature of Evolution? Do I really have to install these extra packages to get this functionality?

---

### Post by Roger Mudd on 2006-09-20
Yes. Out of the box, Evolutions's spam filtering leaves much to be desired.
However, if you're running Dapper (Gnome) like me, Bogofilter and SpamAssassin are most likely already installed. You can verify this by typing the following in terminal:
 
$ which bogofilter
$ which spamassassin
 
Or you can verify by searching in Synaptic Package Manager for the above packages and confirming that their check boxes are ticked.
 
I have used the same HOW TO you linked to above and it has worked very well. In fact, Bogfilter worked so well I didn't even bother with SpamAssassin. Very rarely has spam weasled it's way into my inbox.
 
I found this link (included in the link above) helpful as well:
 
[http://johnleach.co.uk/words/archives/2005/09/15/180/](http://johnleach.co.uk/words/archives/2005/09/15/180/)
 
The screenshots were particularly useful for me.

---

### Post by Stefano Fonzarelli on 2006-11-14
Roger Mudd wrote:

"Yes. Out of the box, Evolutions's spam filtering leaves much to be desired."

I would say, Evolution leavves a lot to be desired in general.

a small list:

- It should not be possible to open Evolution in more than one desktop at a time. Clicking while a copy of Evolution is already running is a recipe for disaster now

- signatures keep dissappearing for no partucular reason

- sometimes it's not possible to add a particular contact to a group

- if you think exporting e-mail from a Outlook to Evolution was a drag, wait until you want to switch to a more grown-up program like Thunderbird. This will surely keep you busy.

For me it seems completely unlogical to include Evolution in the otherwise so great Ubuntu distributions.

---

### Post by Zhukov on 2006-11-23
> **Stefano Fonzarelli said:**
> Roger Mudd wrote:

"Yes. Out of the box, Evolutions's spam filtering leaves much to be desired."

I would say, Evolution leavves a lot to be desired in general.

a small list:

- It should not be possible to open Evolution in more than one desktop at a time. Clicking while a copy of Evolution is already running is a recipe for disaster now


Yes, this is stupid... :D

> **Stefano Fonzarelli said:**
> Roger Mudd wrote:
- signatures keep dissappearing for no partucular reason


I don't know, never used it... :D

> **Stefano Fonzarelli said:**
> Roger Mudd wrote:

- sometimes it's not possible to add a particular contact to a group



All is fine so far :)

> **Stefano Fonzarelli said:**
> Roger Mudd wrote:

- if you think exporting e-mail from a Outlook to Evolution was a drag, wait until you want to switch to a more grown-up program like Thunderbird. This will surely keep you busy.


Now I have to disagree. I've switched from Outlook to Thunderbird to Evolution, to Kmail, back to Evolution, back to Thunderbird, back to Evolution, back again to Thunderbird, once more back to Kmail, quick stop at Thunderbird and now back to Evolution :D

> **Stefano Fonzarelli said:**
> Roger Mudd wrote:
For me it seems completely unlogical to include Evolution in the otherwise so great Ubuntu distributions.

Again, I (somewhat) don't agree. Evolution is the best integrated solution (only?) for Gnome. It works quite ok when it want's to ;)

But yeah, I wish Thunderbird would integrate so nicely in Gnome. :)

---


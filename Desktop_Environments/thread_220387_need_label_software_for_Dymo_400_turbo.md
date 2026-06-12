---
title: "need label software for Dymo 400 turbo"
date: 2006-07-21
forum: Desktop Environments
---

### Post by sitedesign on 2006-07-21
I need to switch a couple more of our desktop PC's in the office to Ubuntu. The problem is they are admin users which need to be able to print address labels using our Dymo Label 400 Turbo printer.

I have the printer set-up on a linux server which is sharing the label printer but now need some label printing software that works under Linux.

Any ideas welcome.

regards Peter King

---

### Post by greenstar on 2006-07-22
> The problem is they are admin users which need to be able to print address labels using our Dymo Label 400 Turbo printer. 
Being an administrator has nothing to do with printing. Further, these people should NOT be administrators if they're having you set up & manage their Ubuntu boxes.

> I... need some label printing software that works under Linux. 
I doubt you'll find your answer in this way. This is the "Windows Way" to approach this problem. There isn't much incentive for anyone to develop linux software for this purpose. There's not enough $$'s in it for Dymo to bother, and most linux users will probably find their solution via one of the methods I will describe below.

I don't know anything about that printer, though I imagine it's a relatively uncommon printer.

After googling I discovered that you didn't even give us the full model name of the printer. If you want help you need to put a little effort into finding information yourself, after all how can anyone help if you can't manage to describe the problem sufficiently. **I spent less than 1 minute on google and found that the full model name of the printer is:**

Dymo **LabelWriter** 400 Turbo

I didn't see any templates on the DYMO website, they want you to use their special software. If you install and configure Wine you may be able to install and print from the Dymo software, though that probably isn't the ideal solution.** It took less than 3 minutes to find this.**

You may need to create templates for the labels you wish to use. Also, you might find some pre-made templates at the printer mfg's site, or you might find that some user has shared templates for your type of printer & media if you google it. You might also look at the website of the company that makes the media you are trying to print on (labels).

Look at the label sheet. It should have a "model number" on it. This model number plugged into google can be very helpful in finding pre-made templates for the job at hand.

For example:
I use Avery mailing labels for my business. So I looked at the package the labels came in and see that the "model number" is 18160 and the dimensions of my labels are 1" x 2 5/8". Below that in small print it says to use template 8160 in Microsoft Word and oither programs. So, I go to avery.com and see that they have a link to their templates right at the top of the home page. I mouse over it, and see that it gives a drop-down menu. I see that the two best options from this list are: Pre-Designed Template Gallery & Blank Template Gallery. So I'd go and browse through their categories until I found what I needed. If no cigar on the pre-designed, then I'd check out the selections in blank templates.

If I were you, I'd look at avery.com to see if I could find a template for labels of the same dimensions as the ones I wanted to use, then just print them to the Dymo printer. As long as the printer is set to use the correct paper dimensions, this should work fine.

I opened up OpenOffice and found that if I clicked on: File->New->Labels there is a label wizard designed to help create custom labels. **This took all of 1 1/2 minutes, including the time for OpenOffice to start.**

I also use templates designed for MS Word & Adobe Acrobat and print from OpenOffice when I need to print labels or non-standard items. If I can't find those, I just make my own. Most times you can google and find templates that need only to be filled in with your text or graphics.

Remember, Google is your friend.

So you can see that it was obvious to me and everyone else on this forum that you couldn't be bothered to help yourself. You didn't even touch google. That's why you didn't get many responses, and also why my response is so terse. I hope this helps you learn a bit of self-sufficiency when it comes to getting assistance with a problem. If you take the time to ask a well though out question, and you have already put a reasonable effort into finding an answer on your own, people will be more willling to help. *You failed to invest even five minutes into your own problem...* that speaks volumes. It shows the community that you do not value our time & collective knowledge. As such, most of us probably smelled the odor of laziness from a quarter-mile away. 

Hope this helps,
Greenstar

---

### Post by sitedesign on 2006-07-30
Apart from being a very sarcy response, I did set-up a template in Open Ofice Writer which seems to work just fine.

The next task I wil pass to our programming department to set-up a report from our CRM system to output a PDF with the page size of the labels and put the contents in. That should solve the problem.

All done.

---

### Post by lemonlovr on 2007-02-14
Well now the top search result on your beloved Google is this very unhelpful thread so I hope everyone is happy.

Considering that there is an open-source approximation for just about every piece of software out there, one would generally be safe to assume that someone in the world has created a Linux version of the Dymo software. Was that too much to ask?

I don't want to create templates in OpenOffice. I've been trying that for 20 minutes now and I can't get the darn thing to switch from Portrait to Landscape. I'm *telling* it to change, but it keeps printing out in the same direction. What would make my life easier is something that only has one job: print labels to my label printer. Unfortunately, I'm not a developor so hopefully there is one out there with a similar problem who will take it upon themselves to make something.

And no, it is not an uncommon printer.

---

### Post by marianlibrarian on 2007-05-18
I know this greenstar wrote this quite some time ago, but ..... there isn't a lot showing up and this is what I get from the mighty google god:
[FONT=Arial, Helvetica, sans-serif]**Dymo LableWriter 400 Ubuntu Linux - Google Search**[/FONT][FONT=Arial, Helvetica, sans-serif]**Google returned no results for this search.** [/FONT]

I have this to say to --------- greenstar ----------------

Jeeeez! Buddy! Take out your frustration and arrogance on some political blog somewhere. Okay??

I am not even going to finish reading your complete reply because it is an insult to -- anyone -- who reads it.

And .... Bless your heart but...

Google is NOT a friend. Google is a search engine tool. If you think something like google is your friend... Well, then that explains your attitude.

I also know that DYMO 400 Turbo this is not an "uncommon" printer. 

If that is the best you can do then say nothing at all.

---

### Post by greenstar on 2007-05-25
This is for marianlibrarian AKA little miss "I'll give you a piece of my mind." Thanks for showing us the diminutive size of that mind. I know my response wasn't very cordial, but there's nothing in it that can be shown to be non-factual. My guess is that you're upset because my post is the most informative you could find relating to your printer and you didn't like the manner in which I provided free assistance. Newsflash: Beggars can't be choosers. I was quite terse, however I also provided the information requested. **Unlike every other response to this thread, I actually had something of value to contribute to the discussion.** Every response except the original author's is just oral diarrhea. At least he told us how he got it straightened out.

> **marianlibrarian said:**
> I know this greenstar wrote this quite some time ago, but ..... there isn't a lot showing up and this is what I get from the mighty google god:
[FONT=Arial, Helvetica, sans-serif]**Dymo LableWriter 400 Ubuntu Linux - Google Search**[/FONT][FONT=Arial, Helvetica, sans-serif]**Google returned no results for this search.** [/FONT][FONT=Arial, Helvetica, sans-serif]

AAaaaaaaahahahahahaha (That's me laughing at the idiot who not only can't copy the name correctly from her printer, but can't even figure out why she can't get better search results.) **Then try spelling the printer name correctly.** Let me guess, your first name is Mo and your family name is Ron, right? (OK, that was uncalled for. My apologies) Also, if your first search doesn't give you the desired result, use different search terms.... duh!
[/FONT] 
> **marianlibrarian said:**
>  I have this to say to --------- greenstar ----------------

Jeeeez! Buddy! Take out your frustration and arrogance on some political blog somewhere. Okay??

I'm not your buddy and it seems you are the frustrated one. After all, it was you that couldn't refrain from posting to an old thread just to start a problem. Grow up. **Everything I wrote in that post is true, and if it's not then disprove it - otherwise shut your pie-hole.** You're welcome to see me as frustrated and arrogant if you like, I could not care less as I've been called worse by better. As they say, opinions are like a-holes, everone has one.

> **marianlibrarian said:**
>  I am not even going to finish reading your complete reply because it is an insult to -- anyone -- who reads it.

That's too bad because it is likely to be the most informative regarding this particular problem.  I bet it really made you mad that I'm the only one on the entire forum that even bothered to try and help. I should care that you're not going to get the answer you were after because... that answer insults you? If the shoe fits, wear it. I said what I did because it seemed obvious to me that the original poster hadn't bothered to try to find anything on his own, but was rather trying to get someone to do it for him.  This displays laziness and a lack of respect for other people's time. (My assessment could have been in error, but I doubt it.) People (myself included) are far more willing to help when it can be seen that the person in need is actually making efforts themselves.

> **marianlibrarian said:**
>  And .... Bless your heart but...

Wow, you make this so easy... 

That's one of the weakest attempts at asserting superiority that I've ever seen.

> **marianlibrarian said:**
>  Google is NOT a friend. Google is a search engine tool. If you think something like google is your friend... Well, then that explains your attitude.

My usage of friend is widely accepted in the context above. If a dog or cat can be your friend, so can Google. Also, Google isn't a "search engine *tool*" it's definitely a search engine, and most would agree it can be used as a tool. But a "search engine tool" it isn't. That's as illiterate a statement as this: "Estwing makes great hammer tools." Estwing makes fine hammers, which can also be considered tools, but they are most definitely not "hammer tools". Duh! This is also why we do not refer to our automobiles as "car vehicles" or our pickup trucks as "truck haulers", etc. Since I have to explain all of this for you, maybe you should get friendly with Google, you might just learn something.

> **marianlibrarian said:**
>  I also know that DYMO 400 Turbo this is not an "uncommon" printer. 

Really? So you must know many people that have one of these, then? And they probably are available anywhere printers are sold, right? (I can barely contain my laughter!) I know *all* of my friends have Dymo label printers.:wink:  **In fact, of all the businesses I service in my area, only *one* has one of these printers**, and even they only use it occasionally, so yes, this is an uncommon printer. It doesn't matter if it is Dymo's most popular model, it's still an uncommon printer; even if Dymo sold 500,000 units, it's still an uncommon printer.

> **marianlibrarian said:**
>  If that is the best you can do then say nothing at all.

I have earned the privilege of saying whatever I like, whether you like it or not. When you've sacrificed as much as I have for your fellow man, you can feel free to say what you like as well. (Though I'm sure that won't stop the diarrhea from pouring out of your mouth.) *Please* ask me how I've earned that privilege.

As a librarian, I'm willing to bet you've not contributed much to your fellow man. This **is probably the best you can do,** so I won't hold it against you.

---

### Post by marianlibrarian on 2007-05-25
Dear Greenstar,

My goodness, you really are full of it. I hope you feel better after that dump. :D

---

### Post by greenstar on 2007-05-25
Yes, I do, thanks for asking. And yes, I'm full of it... if: 

A. *it* is annoying people who have nothing better to do than to start problems with people they don't know from Adam, while adding nothing of value.

and

B. by *full* you mean as in "fed up" or "sick & tired".

9 times out of ten, I provide help in a friendly, easygoing manner. However if someone is... less than courteous/respectful of those providing said help, I've no difficulty with a bit of abrasiveness myself. I'm not a sit down & take it kind of person. I also will usually help anyway because most times an answer to a problem can be useful to not only the original poster, but other users as well.

---

### Post by greenstar on 2007-05-25
That being said, I have something unrelated to add. 

> **marianlibrarian said:**
>   				Have an open mind. Your brains will not fall out. Information at the library is free. Bring your own container.

I really like this part of your sig., couldn't be more true. Also quite funny in a sad kind of way. Some people have never set foot in a public library.


> **marianlibrarian said:**
>  I am a librarian: Installing 9 new computers in our rural library that will only have Dapper Drake on them. 

I admire your efforts to open source the library, for many reasons. Not the least of which is the reduction of expenses to whatever entity funds your library. (Usually the taxpayers.) I tried talking to the administration in my local library about keeping a few sets of Ubuntu CD's available for circulation, and was going to bring up the idea of installing Ubuntu on the public access PC's next. I talked to 3 or 4 people, and they wouldn't entertain the idea of Ubuntu available for checkout. It seemed like they were actually scared of the idea. I had even taken care of acquiring the discs ahead of time, but nothing doing. Anyway, with that much resistance to free CD's available for checkout, I knew open-sourcing the public kiosk PC's wasn't gonna have a snowflakes chance...

Any suggestions? I should actually start a new thread and discuss this very subject. I believe it's an excellent place to start introducing the community to FOSS.

---

### Post by Qchan on 2008-07-10
[b][color=darkred]
lol! GreenStar, you are hilarious!!

Anyway, I found an answer to all of you who are having problems with this printer. I came across this because I wanted to see if this worked in Linux too (duh?!), however, I do not own this printer. I was just looking out of curiosity.

Anyway, here is the link:
[http://forums.freestandards.org/read.php?33,120](http://forums.freestandards.org/read.php?33,120)

Many people have reported they've got their Dymo Label printer working!
Happy printing!
[/b][/color]

---

### Post by marianlibrarian on 2008-07-11
Finally!

[COLOR=DarkRed]**Thank you**[/COLOR] for coming back and posting this information. That is all I wanted. Our old electric typewriter finally died and I had to do something.I gave up here and purchased a laptop that came with vista and installed the Dymo 400 and it works fine. It is awkward though sometimes, we also use this laptop downstairs to check in / out our children's books. It will be nice to have the new book processing done all on one Ubuntu  computer. 

P.S. All of our public access computers are Ubuntu 6.06, we currently have 5 available to the public. In the month of June we had 636 users. We are open M - F 9:00 - 5:30. Our town only has 4,300 population. Everyone is coming to the library these days. A couple of years ago we had maybe 100 people in the month of June. Our patrons LOVE Ubuntu and so do I.

---

### Post by Qchan on 2008-07-12
> **marianlibrarian said:**
> Finally!

[COLOR=DarkRed]**Thank you**[/COLOR] for coming back and posting this information. That is all I wanted. Our old electric typewriter finally died and I had to do something.I gave up here and purchased a laptop that came with vista and installed the Dymo 400 and it works fine. It is awkward though sometimes, we also use this laptop downstairs to check in / out our children's books. It will be nice to have the new book processing done all on one Ubuntu  computer. 

P.S. All of our public access computers are Ubuntu 6.06, we currently have 5 available to the public. In the month of June we had 636 users. We are open M - F 9:00 - 5:30. Our town only has 4,300 population. Everyone is coming to the library these days. A couple of years ago we had maybe 100 people in the month of June. Our patrons LOVE Ubuntu and so do I.

[b][color=darkred]
I apologize that you had to wait for over a year for a proper answer.
The other guy was definitely a loser. Please don't feel that the rest of us here are anything like that guy.

I'd also recommend upgrading your systems to Hardy Heron (8.04 LTS). From what I understand, Hardy supports the printer natively.
[/b][/color]

---

### Post by marianlibrarian on 2008-07-13
>  I'd also recommend upgrading your systems to Hardy Heron (8.04 LTS). From what I understand, Hardy supports the printer natively.

Really! Yippee! The one computer I need this printer on is a staff / work computer. I had planned on keeping with Dapper Drake due to the support, however, maybe just one computer with something different will be OK. 

So DOUBLE Thank You for the information!

And you are right green star is an exception here. Most people are very kind and patient and understanding in this forum. It is a shame that he liked my signature but didn't understand that an arrogant mind is never open.

---

### Post by bpalone on 2008-07-19
I put together a How-To for installing the CUPS drivers from DYMO, it is located here:
[http://ubuntuforums.org/showthread.php?t=861781&highlight=dymo](http://ubuntuforums.org/showthread.php?t=861781&highlight=dymo)

Hope it helps you or anyone else needing to get a DYMO printer working.

---


---
title: "2 Questions - Evolution Rules &amp; Firefox Pop-Ups"
date: 2009-03-12
forum: General Help
---

### Post by DannyP87 on 2009-03-12
Hi everybody, still quite new with Ubuntu so please bear with me if these questions are stupid or have already been answered.

**1. Creating a Rule in Evolution**
I currently have a newly created gmail account which I've set up with Evolution and works great. The majoroity of my emails right now are from Facbook and I now want to put them into it's own folder for the ones I've recieved and the ones in the future.

The emails which I already have I've manually moved them over by selecting them all with Ctrl as you would in Windows then dragging them into a new folder I've created in the inbox called Facebook.

I've looked at the create rule option but can't get my head round it for it to work. Facebook emails come from usually emails ending @facebookappmail.com, @facebookmail.com or @cs.slide.com. So if possible I'd like to send any emails containing them email addresses to the new folder. Any ideas?

**2.Blocking unwanted pop-ups in Firefox**
For some reason, in my opinion Firefox pop-up blocker is literally rubbish compared to Operas.

I don't use it that often but for some reason when I do use it some pop-ups open up in a new window (Which I hate) and can take the whole screen up and pressing F11 doesn't minimize them. It's strange as usually when this happens it's a link I press which I want to open in a new tab, and along comes the full window ad. I've checked the pop-up blocker settings and there all as they should be this is sooooooooo annoying, is there any plugins available for Firefox to completly stop pop-ups.


Very very sorry guys for the complete essay but if anyone can help i'll be truely greatful. 

Ta, Dan

---

### Post by x C0MMAND0 x on 2009-03-12
Are you using Adblock Plus?

[https://addons.mozilla.org/en-US/firefox/addon/1865](https://addons.mozilla.org/en-US/firefox/addon/1865)

Then subscribe to the EasyList USA upon firefox reboot when it prompts you.

That works fine for me.

---

### Post by DannyP87 on 2009-03-12
Thanks Commando thats the block ups sorted :)

Anyone know about the rule?

---

### Post by plucky on 2009-03-12
In Evolution go to **Edit > Message Filters > Incoming > Add** Give the Rule a title e.g Facebook.

Then add as many Criteria as you require,and select "If any Criteria are met"

In the Criteria window, select 
1)Recipients Contains @facebookappmail.com
2)Recipients Contains @facebookmail.com
3)Recipients Contains @cs.slide.com

etc. as many as you need

and then in the "Then" window, select 
Move to Folder Inbox/Facebook  or whatever the folder is called.

It will give you the list of your folders.


It should then look at all your email and any that addressed with your Criteria will be directed to the "Inbox/Facebook", all the rest will be directed to "Inbox".Tune as required

Hope you understand!!!

Or you could add rules for the rest to go elsewhere. 

Good luck

---

### Post by DannyP87 on 2009-03-12
> **plucky said:**
> In Evolution go to **Edit > Message Filters > Incoming > Add** Give the Rule a title e.g Facebook.

Then add as many Criteria as you require,and select "If any Criteria are met"

In the Criteria window, select 
1)Recipients Contains @facebookappmail.com
2)Recipients Contains @facebookmail.com
3)Recipients Contains @cs.slide.com

etc. as many as you need

and then in the "Then" window, select 
Move to Folder Inbox/Facebook  or whatever the folder is called.

It will give you the list of your folders.


It should then look at all your email and any that addressed with your Criteria will be directed to the "Inbox/Facebook", all the rest will be directed to "Inbox".Tune as required

Hope you understand!!!

Or you could add rules for the rest to go elsewhere. 

Good luck

Thanks plucky, I'll just wait for an eamil from Facebook and let you know how it got on.

Thanks again! ;)

---

### Post by DannyP87 on 2009-03-13
Hi there, tried what you said but unfortunately it doesn't seem to be working :(

I've attached an attatchment of a screenshot of what I have put in the boxes.



Ta, Danny

---

### Post by DannyP87 on 2009-03-13
Anyone? 


Pretty pretty please!

---

### Post by plucky on 2009-03-13
> Hi there, tried what you said but unfortunately it doesn't seem to be working

I've attached an attatchment of a screenshot of what I have put in the boxes.


What you have is basically correct,but you could use the whole email address.

Why don't you try other things,like using **is** instead of **contains** and use the full email addresses.(if you do don't post a screenshot)

Look at the emails and pick out something in the To addresses that are always there and you can use.

The Rules are just logical If/Then steps to move the email to where you require.

What I have posted are only examples,I didn't expect you to use them literally as I can't see your actual configuration.

Good Luck

---


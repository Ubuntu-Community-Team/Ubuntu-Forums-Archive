---
title: "Evolution Message Filter"
date: 2005-12-16
forum: General Help
---

### Post by Sutekh on 2005-12-16
I've been trying to get my message filters working for ages, I know there are lots of people who having it working, so I need all you to point out what's going wrong.

I basically want to filter messages incoming to a ceratin folder if they are from a certain sender.  For example, when the forums send me an email about a thread notification I want it sent to a folder just for these notifications.  

So here's what I have;  IF "sender" is "site@ubuntuforums.org" THEN "Move to Folder" "Ubuntu Forum Alerts".  Yah, simple.  Now if I have a message in my Inbox that meets this rule, and I press Ctrl+Y (Apply Filters) and off it goes to the folder I want. 

BUT

I have to do this for EVERY single email, it won't do all of them in one go.  
Also it won't automatically apply the filters when the mail is checked.

So can anyone help me with this?  
(Pic shows the filter, so hope that helps)

dcstar, I know you got it working, help a fellow Aussie?? [-o<

---

### Post by Sutekh on 2005-12-18
I worked on this most of the weekend, and have some sort of progress.  

I use Evolution with two email accounts, a personal and a work email.  

I've set up a filter so that email for each account would be moved to separate folders using the 'Source Account' filter.  When I get new mail its sorted automatically into the corresponding folder. 

However the 'Forum Alert" filter doesn't work automatically, the emails are moved to my work email folder using the 'Source Account' filter, but they stay there.  I can apply the 'Forum Alert' filter manually to move them to their own folder, but I have to do this for each and every email.  So still no go.

---

### Post by Sutekh on 2005-12-19
YEAH SOLVED!

It was the *order* of my filters that was messing things up.  

My mail was filtered into the folder from each source account, but then it was trying to filter mail, that was already diverted into a different folder.  

So now Evolution filters the forum alerts (and other specific filters) first, then the rest of the mail.

---


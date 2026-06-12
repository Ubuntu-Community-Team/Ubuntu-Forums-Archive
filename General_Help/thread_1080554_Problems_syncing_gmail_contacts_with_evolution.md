---
title: "Problems syncing gmail contacts with evolution"
date: 2009-02-25
forum: General Help
---

### Post by andyanderso on 2009-02-25
I want Evolution to use my gmail contacts as an online address book. I tried following the guide [here]("http://library.gnome.org/users/evolution/stable/usage-contact-cards.html.en#b1dl9th7").
However when I go to use the address book I get this error:
> "We were unable to open this address book. This either means you have entered an incorrect URI, or the server is unreachable."

I have tried googling for answers and searching here. I have not been able to find anything.

I can import contacts as v-cards for now.

Everything else connects just fine - Gmail imap, and Google Calendar -still can't see repeating events though - some day right;)

---

### Post by andyanderso on 2009-03-03
Anyone else have this problem?

---

### Post by Roanoke on 2009-03-03
Try exporting the contacts as .csv.

---

### Post by andyanderso on 2009-03-07
Exporting the contacts as a csv works fine. However I really want an online address book. This way when I use gmail on the internet and create contacts they will show up in my evolution address book without me having to update it....

---

### Post by Roanoke on 2009-03-08
Aaah, I didn't understand you at first. Sorry, but I have no idea.

---

### Post by kaps81 on 2009-03-10
Hi andyanderso,

the same problem here. I'm not able to sync Evolution with Googlemail contacts (for legal issues GMail is termed Googlemail here in Germany).

Sometimes i get the same error you mentioned and from time to time a SEG FAULT occurs...

It happens on a 32-bit Intrepid as well as on a 64-bit system...

evolution 2.24.3-0ubuntu1
evolution-data-server 2.24.3-0ubuntu1

---

### Post by bchalstrom on 2009-03-12
I am getting the same problem.

---

### Post by tdmoore on 2009-03-12
I just tried it tonight for the first time following the guide and it worked fine.  Thanks for the tip.
Ubuntu 8.10, Evolution 2.24.3.  We run inside Google Apps for domain.

However, I do have a problem that seems to be recognized in your posts as well and that is with the calendar.

I can see SOME of my events on my calendar inside Evolution but not all and certainly not repeating.  I do get to see events that I have been invited to by colleagues too...pretty funny that some public events show and others don't.

Any suggestions anyone?  Evolution would clearly be my choice but I live on my calendar app.

Thanks in advance.

---

### Post by johny_ on 2009-06-02
Hey,

Importing gmail contacts online worked for me too.
Maybe you've got an old version of Evolution Andyanderson?
Have you tried to upgrade?

---

### Post by revcp on 2009-06-03
I'm using evo 2.26.1.  Syncing with google calendar is flawless.  When I sync with gmail contacts, however, (using this guide: [http://www.linux.com/news/software/applications/8226-how-to-sync-evolution-with-googles-pim-apps](http://www.linux.com/news/software/applications/8226-how-to-sync-evolution-with-googles-pim-apps)) I get full name field and nothing else even though my gmail contacts are fully filled out.

Any ideas?

---

### Post by nandotron on 2009-06-17
thought i might add my 2 cents to this:  for you guys who've gotten this to work, does evolution sync with 'all contacts' in gmail?

mine does this, but it's not ideal, i'd rather get it to sync with 'my contacts' so that it doesn't store addresses of every single person i've emailed...

any thoughts?

---

### Post by bertmanphx on 2009-07-03
Hello,
I just started having this problem.  Actually, it began when I changed my Gmail password.  All three elements asked for my new password withing Evolution, Mail, Calendar, and Contacts.  However, since that password change, the I get the same error message regarding a "URI" not being correct.

Anyone find the fix for this?

Thanks,

bertman

---

### Post by antono on 2009-07-12
> **bertmanphx said:**
> Hello,
I just started having this problem.  Actually, it began when I changed my Gmail password.  All three elements asked for my new password withing Evolution, Mail, Calendar, and Contacts.  However, since that password change, the I get the same error message regarding a "URI" not being correct.

Anyone find the fix for this?


[COLOR="Red"]Yep. Open alt+F2, seahorse. Than go to passwords tab and find password with google:// scheme. It seems that gnome-keyring stores old password for contacts. Delete this stored password and try access your addressbok again. It will ask for new password.[/COLOR]

---

### Post by bertmanphx on 2009-07-12
Antono,
I had to delete the entry for my Gmail contacts in Evolution and re-add it.  After that, all worked well. 

Thanks!

bertmanphx

---

### Post by antono on 2009-07-13
> **bertmanphx said:**
> Antono,
I had to delete the entry for my Gmail contacts in Evolution and re-add it.  After that, all worked well. 

Thanks!

bertmanphx

Please, indicate that this bug affects you too :)
[https://bugs.edge.launchpad.net/ubuntu/+source/evolution/+bug/385935](https://bugs.edge.launchpad.net/ubuntu/+source/evolution/+bug/385935)

---

### Post by jfolpf on 2009-10-04
> **antono said:**
> [COLOR=Red]Yep. Open alt+F2, seahorse. Than go to passwords tab and find password with google:// scheme. It seems that gnome-keyring stores old password for contacts. Delete this stored password and try access your addressbok again. It will ask for new password.[/COLOR]

Hi, sorry for disturbing, but I already updated all my passwords on Applications->Accessories.>Passwords and Encryptions Keys, I already set in Evolution mail File->Forget Passwords to reset any possible mistaken password, and then when I tried to sync my address book in Evolution with Google, it gives me the initial error. I'm sure I inserted the correct password, I put my user without @gmail, I hit the ssl box, and it gives me "Error loading address book" with something related to an incorrect URI.

I'd really like to sync my Gmail contact list with Evolution Mail 

I would kindly appreciate your help

---

### Post by gergos on 2009-10-04
I have tried everything listed here including completely deleting my google account in evolution, completely removing evolution and readding it and seahorse passwords - I re-added google mail and still get the URI error (other error is listed - whatever that means!)....  
I have a G1 and HAVE to have this working - why it stopped is nobody's clue!

---

### Post by bertmanphx on 2009-10-05
Hello,
I solved the syncing of the contacts with the solution using Seahorse as listed above.  Interestingly, I just started having a problem with my Google Calendar syncing........

I could not solve that issue the same way, so I entered my Google Calendar as a caldav item.  Now it works.

bertmanphx

---

### Post by Rasheeke on 2009-10-05
Same Issue here.

Error loading address book.

This address book cannot be opened.  This either means that an incorrect URI was entered, or the server is unreachable.

Detailed error message: Other error

Don't know why.  I guess I can try other methods but I would prefer to have an online contact list that will always automatically update.

---

### Post by jfolpf on 2009-10-05
> **bertmanphx said:**
> Hello,
I solved the syncing of the contacts with the solution using Seahorse as listed above.  Interestingly, I just started having a problem with my Google Calendar syncing........

I could not solve that issue the same way, so I entered my Google Calendar as a caldav item.  Now it works.

bertmanphx

I already deleted all my passwords using Seahorse, as listed above, I synced my contacts again using the correct password and I have the some error related to URI "Error loading address book". My password is correct, as I read and send emails correctly with no problem using IMAP from Gmail

I would kindly appreciate your help

João

---

### Post by newb85 on 2009-10-05
I've been experiencing this problem, too.  I have tried all the suggestions here, to no avail.  Contacts and Calendar both quit working at the same time for me, but I can get Calender to work using caldav.

Could the issue have something to do with the fact that evolution keeps changing my username into my full email address?

---

### Post by bertmanphx on 2009-10-06
Ok,
I have NO idea is this was the fix or not.  I was looking for other ways to have an online calendar....sync with my other Horde email server's calendar....putting one on box.net.....and such.

I installed "syncml", restarted Evolution, and added my Google calendar.  Now it works.
I do not know if this was a fix, or it is was simple a coincidence.

Can somebody confirm?

bertmanpx

---

### Post by jfolpf on 2009-10-06
> **bertmanphx said:**
> Ok,
I have NO idea is this was the fix or not.  I was looking for other ways to have an online calendar....sync with my other Horde email server's calendar....putting one on box.net.....and such.

I installed "syncml", restarted Evolution, and added my Google calendar.  Now it works.
I do not know if this was a fix, or it is was simple a coincidence.

Can somebody confirm?

bertmanpx

Ok, you have your google calender working, but can you sync your contacts from google gmail with your Evolution Contacts? If so, what did you do?

Regards

---

### Post by bertmanphx on 2009-10-06
Hello,
Honestly, I didn't try the Google Contacts until just now....although ti's been setup, it's not my default addressbook.  It prompted my for my password, and seems to work just fine.

bertmanphx

---

### Post by jfolpf on 2009-10-07
Finally I put it working :)

I just did what you mentioned. I had to go to "System->Administration->Synaptic Package Manager" and I had to install "syncml". Then I synchronized my Gmail contacts with Evolution and it worked just fine :)

It was missing "syncml" on my system...

Problem solved :)

Thanks a lot

João

---

### Post by emigrant on 2009-11-16
hi all,
another way to solve the problem without installing any additionals:

**Getting Gmail contacts synchonised in Evolution**

 This setting will allow a user to see his Gmail contacts in Evolution (even for offline use). This method creates a new address book that synchronises with Gmail contacts. 

[LIST=1]
[*]On the Evolution Contacts window, select the **New** drop-down menu and choose **Addess Book**. The New Address Book window will appear. 
[*]Ensure that **Type** is set to **Google**. 
[*]In the **Name** field, enter a name for the new calendar. 
[*]In the **Username** field, enter your Google username. This will be something like [email]username@gmail.com[/email]. 
[*]Check **Use SSL**. 
[*]Click on the OK button. 
[/LIST]
The new address book should then be displayed in the Contacts list under Google. Existing contacts should be shown and new contacts synchronised. 

[https://help.ubuntu.com/community/Evolution](https://help.ubuntu.com/community/Evolution)

---

### Post by samfowler11 on 2010-12-07
Hi,

Did anyone find a solution to this problem? I am having the same problem and installing syncml didnt solve it.

---

### Post by amirfluid on 2012-06-03
I had the same problem. I installed the following plugin and now it works like a chatm :)

office productivity suite -- Evolution addressbook support

---


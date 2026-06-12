---
title: "can't use distribution lists ('groups') in kaddressbook/kmail"
date: 2010-12-04
forum: Desktop Environments
---

### Post by sanette on 2010-12-04
Did anyone manage to use distributions lists (called "groups") in kaddressbook ?  (in Kubuntu 10.04)

I can't imagine an email client without this feature, but here it is:

* in kaddressbook I can create a new group and add email adresses in it. Say I call it "Family"

* now I expect to right-click on it and have a menu giving me the possibility of "send an email to the group"...
nope.

* OK, I go to kmail, new message, and on the right of the address slot, I click on "select". Then ah! it seems I can select my "Family" (now it's called a "distribution list"). I click "Add", and now my recipient is  "Family"...
I'm a bit suspicious, but OK, let's send the message...

of course it doesn't work: I immediately get
 <Family@my-laptop>: Recipient address rejected: Access denied

No kidding ... ;)

* OK, I want to do it again, but now after "select", I am curious and open the "Family" list (by clicking on the "+" on the left). Surprise: most of my contacts in it appear empty (yes, empty lines) !
But not all of them...So I can't even manually select them all.

* Conclusion: groups of contacts (or distribution lists) are completely screwed up in kubuntu 10.04.
But this is such a basic and essential tool !

How do you guys cope with this ??? :confused:

*(crossposted from kubuntuforums.net : I had no luck there)*

---

### Post by mardukvmbc on 2010-12-08
*Bump!* I have the same problem and it's driving me nuts!!
Also the "Save as list" button in kmail doesn't actually save the list -- it doesn't show up in Kontacts at all.
Groups are seriously broken in Kontact/Kmail.
I'm on 10.10 (KDE 4.5.1)

---

### Post by chaanakya_chiraag on 2010-12-08
I decided to go completely CLI (command-line interface) and am now happily using Mutt + Emacs + a custom script I wrote (inspired by the Windows program febootimail) which can be found here: [http://ubuntuforums.org/showthread.php?t=1378583](http://ubuntuforums.org/showthread.php?t=1378583)

---

### Post by mardukvmbc on 2010-12-09
Thanks for that but my wife loves kmail and so do I... I'm surprised groups don't work.

---

### Post by chaanakya_chiraag on 2010-12-09
I wouldn't know - I use "vanilla" Ubuntu, which uses GNOME and Evolution - I'm not exactly sure how groups work in Evolution either, but I basically gave up on any/all GUI email clients :D

---

### Post by andreselsuave on 2010-12-14
Im using kmail too and I'm having the same issue. I've found on other kde forums that the same issue was there around 2007. It was eventually fixed, but looks like it's broken again.

I will subscribe in case there are news =)

good luck guys

---

### Post by mardukvmbc on 2010-12-14
Just upgraded to KDE 4.5.4 via PPA and no difference. I'm wondering if I should go to 4.6 beta or if it's config and not a KDE bug?

---

### Post by mardukvmbc on 2010-12-14
Just upped to 4.5.85 (4.6 Beta2) and no joy. It must be a config issue, can't imagine groups still don't function in kmail 2.0.89.

---

### Post by mardukvmbc on 2010-12-14
Got groups working by removing soprano-virtuoso.trx but it's a hollow victory. All my groups disappear from the address book as soon as I log out.
Groan!! This was also happening under KDE 4.4 and 4.5.
Aknonadai/Nepomuk drives me crazy!!!

---

### Post by mardukvmbc on 2010-12-14
So I did the full monty and blew away the .kde folder in home to start from scratch. After 2 hours fiddling with akonadi settings to get it to stop migrating over and over I've gotten nowhere.
Hard to believe groups don't work over so many versions of the kde pim stuff, but it's also hard to believe that it's a config issue after I've started from scratch with a fresh .kde folder.
Also hard to believe akonadi is so finicky.
"Groups" is greyed out in the default address book, so I created a new one. It lets me create groups but they're gone in the next login. 
"Save to list" in kmail does nothing.
Oh, but if I do send to a group in the same session that I created the group in, it does work!

---

### Post by Nozdriov on 2011-03-30
Hello,

I also have problem with distributions list in Kontact/Kmail/Kaddressbook.

Here is what I realise, this might help to find a solution:

If a create a new list and add names to it and use autocompletion. I will then see the correct mail adresses but the small icon on the left is not like an envellop (like it is if I add new adresses which are not in my adressbook).

Then when I had the list in a field to/cc/bcc it will send mail to name_of_list@name_of_computer, like everyone seems to say. However, if I edit the list and change names to names which are not in my adress book (let's say First Name instead of First_Name  Last_Name) there the icon appears correctly and I can select the list and it will send the message to the correct recipient.

I don't understand the reason of that, and I don't like this workaround a bit.

---


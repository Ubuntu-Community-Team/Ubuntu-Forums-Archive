---
title: "Evolution, ldap, and autocomplete"
date: 2006-02-17
forum: Desktop Environments
---

### Post by jasonanovak on 2006-02-17
So I've been playing around with both evolution and thunderbird, and I was wondering what evolution's ldap behavior was suppose to be.

What I mean is the following:
In Thunderbird, if I add an ldap directory to my addressbooks, when I write e-mails, it will autocomplete address from the ldap directory based upon name. (I.e. in the to field I write "John Doe" and it returns "johndoe@addressinldap.com")

When I add a ldap directory in evolution, I cannot seem to search the ldap directory from either the address book, nor does it autocomplete when I type in e-mail addresses. I imagine that the first part is not standard behavior, but I am curious if the autocomplete behavior is standard / evolution doesn't have that sort of autocomplete functionality.

Thanks,
Jason

---

### Post by kaamos on 2006-02-17
Hello!

You have to set the autocomplete on as it is not enabled by default. Look in evolution preferences.

---

### Post by jasonanovak on 2006-02-17
Sorry, I should have added that I had in fact enabled autocomplete on that ldap addressbook, and I still don't seem to have any sort of actual autocomplete occuring.

Should I be expecting the same sort of autocompleting in evolution that I see in thunderbird (i.e. obviously completes the e-mail address in the compose window), or does it operate in some other manner?

Additionally: are there packages that I should have installed to have ldap autocomplete enabled?

Thanks,
Jason

---

### Post by dcstar on 2006-02-17
[QUOTE=jasonanovak]Sorry, I should have added that I had in fact enabled autocomplete on that ldap addressbook, and I still don't seem to have any sort of actual autocomplete occuring.

Should I be expecting the same sort of autocompleting in evolution that I see in thunderbird (i.e. obviously completes the e-mail address in the compose window), or does it operate in some other manner?

Additionally: are there packages that I should have installed to have ldap autocomplete enabled?

Thanks,
Jason[/QUOTE]
If the ldap stuff listed in the "Contacts"?

---

### Post by jasonanovak on 2006-02-17
Ok, so new status update:

I've enabled Autocomplete for the LDAP addressbook from preferences. Now, when I'm in the Contacts pane and search the LDAP addressbook, I now get results. However, when I write e-mails, if I enter names into the "To:" field, the LDAP doesn't autocomplete them to e-mail addresses. For the sake of comparison, this does work in Thunderbird.

Any suggestions?

Thank you,
Jason

---

### Post by dcstar on 2006-02-17
[QUOTE=jasonanovak]Ok, so new status update:

I've enabled Autocomplete for the LDAP addressbook from preferences. Now, when I'm in the Contacts pane and search the LDAP addressbook, I now get results. However, when I write e-mails, if I enter names into the "To:" field, the LDAP doesn't autocomplete them to e-mail addresses. For the sake of comparison, this does work in Thunderbird.

Any suggestions?

Thank you,
Jason[/QUOTE]
Close and restart Evolution and see if it works.

---

### Post by jasonanovak on 2006-02-17
[QUOTE=dcstar]Close and restart Evolution and see if it works.[/QUOTE]

I've restarted Evolution, and it still doesn't work.

Maybe I missed something in the setup of the LDAP addressbook?

I did the following:
Went to Contact, went to "On LDAP Server", right clicked to create a new address book, chose the "On LDAP Server" type, filled in my ldap server information, and I changed the search scope to Sub. If the search scope was one, then it failed completely, and trying to search in the contacts pane returned nothing.

From this point, I went to Preferences, and I enabled AutoCompletion on the LDAP server that I just added. (It is also enabled on my local address book if that matters.)

I then restarted Evolution and tried to compose a message. In the "To:" field, I wrote the name of someone I know is in the LDAP directory; however, the person's name is not converted into their e-mail address.

Am I missing some obvious step?

Thank you for all the help.

Jason

---

### Post by kadissie on 2006-06-06
I'm also having this problem.  I have people in my address book, I have autocomplete ticked in Preferences, and yet when I type in a name in a new email there is no autocompletion.  I have restarted Evolution several times.

I have also added the evolution-plugins package, which gives me the "automatic contact" functionality when I reply to an email.  That works, so there are plenty of people in my address book, but I can't access them (except from the Contacts pane)!

I'm using Xubuntu 6.06 and an IMAP mailserver.

Robert.

---

### Post by superdexter on 2006-06-14
I am not using LDAP for my address book and found the same behavour as kadissie did.  I would use autocontacts plugin or even the right click on address and "add to contacts".  This would succesfully add the contact if I would go view the contacts page, however autocomplete in a new message did not work.

I have found that if I ...
1.) open the individual contact details for full edit
2.) add a space to blank field and remove it.
3.) save the "unchanged" details back. 

...then the autocomplete in new email message works as expected.  I am looking to see if there is a true fix.  I have updated the address book permissions:
~$ cd .evolution/addressbook/local/system/
~$ chmod 744 *

reloaded evolution and it behaves the same way still. 

Ever searching,
superdexter

---

### Post by superdexter on 2006-06-14
I have just fixed my issue of autocomplete not working by selecting the Personal address book as default.  Now all works the way it should. This is done by going to Contacts -> right click on the Personal address book under "On this Computer" -> properties, and then adding the checkbox for "Mark as default folder".

I hope this helps also with LDAP address books.  I do not have any to test with.

Regards,
Emmett

---

### Post by setterm on 2007-04-14
Hi all,

ok so it's quite late, so please excuse me if i'm off track here. But I was having quite some issues with Evolution and OpenLDAP resolution also. I setup openldap on one server and ldapsearch, lat, luma and thunderbird addressbook could query it, but not Evolution.

What I did that finally got it working was to ensure that you have an ** ip address**, **not a hostname** for the ldap server and set "**mark as default folder**" in the server properties. It appears - without specific investigation - that evolution won't do a hostname resolution for ldap servers. 

Once i did this, all works very well indeed.

cheers,

Matt

---


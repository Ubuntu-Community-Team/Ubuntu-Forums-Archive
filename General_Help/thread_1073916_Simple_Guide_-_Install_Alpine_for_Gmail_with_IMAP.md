---
title: "Simple Guide - Install Alpine for Gmail with IMAP"
date: 2009-02-18
forum: General Help
---

### Post by slumbergod on 2009-02-18
I find alpine useful for email when my broadband connection quality is lacking. Whenever I go to install it, I find it difficult to find a concise but simple set of instructions for configuring it in one place - they are scattered all over the place and many are very much out-of-date. This is the simple set I use which works for me and may help others in the future.

1. Install alpine with:
   sudo aptitude alpine
2. If you want to be able to save your password for logging into your inbox and for sending you need to create a blank password file. If you are not confident that your security is adequate you might want to just skip this step and enter it each time you are prompted.
   cd ~
   .pine-passfile
3. Start alpine from the prompt by typing 
   alpine
4. Move into the configuration menu (M-S-C key strokes) and enter the following information:
   User ID: [email]your_username@gmail.com[/email]
   User Domain: gmail.com
   smtp server: smtp.googlemail.com:587/tls/user=your_username@gmail.com
   Inbox Path: imap.gmail.com:993/ssl/user=your_username@gmail.com
	(alpine will ask which inbox you want to use. 
         Just press Enter here to use the default "inbox)

   (note: 587/tls and 993/ssl were obtained from gmail's imap help page)

5. Continue through the rest of the options and set anything else you desire. Ctrl-G on a highlighted field gives an explanation of that setting. 

Most people online seem to set these:
   [Advanced User Preferences] 
      check "Save Will Not Delete"
      Pruning Rule: check "Don’t rename, don’t delete" 
If you press 'w' for Where Is, you can partially type a search string to just straight to it. 
6. Exit settings, making sure to save them when you are prompted. Restart alpine. You'll be prompted to enter your password when alpine logs in and attempts to retrieve your inbox listing. Also, when you go to send a mail you'll get prompted. Because you have a passfile created you'll get the option of saving them for future use.
NOTE: the address book isn't retrieved from gmail and I have never found a way to do this. Instead, when you receive a new email and are viewing it, pressing 'T' will present a list of all the email address you wish to "take" from the mail for storage in your address book.

Hope that helps. If you have more tips that work with Alpine 2.0 go ahead and add them.

---

### Post by uberkermit on 2009-08-17
First of all, thanks for the useful guide.  I have tried several different Alpine/Gmail howtos, and none really worked for me.

> **slumbergod said:**
> 
NOTE: the address book isn't retrieved from gmail and I have never found a way to do this. Instead, when you receive a new email and are viewing it, pressing 'T' will present a list of all the email address you wish to "take" from the mail for storage in your address book.


As to the address book, [this]("http://pinguin.uni-psych.gwdg.de/%7Eihrke/wiki/index.php/Installing_and_configuring_pine#Getting_GMail_Contacts_into_Pine") is a way, albeit somewhat hacky...  I should add that I did not actually try it, so YMMV.

> **slumbergod said:**
> 
User ID: [EMAIL="your_username@gmail.com"]your_username@gmail.com[/EMAIL]


I did not have the User ID field in my Alpine (version 2.00) - I ended up changing the username on my local machine to match my gmail account username.  Does anyone have any help for a solution to this?

---

### Post by DMcA on 2009-08-18
> I did not have the User ID field in my Alpine (version 2.00) - I ended up changing the username on my local machine to match my gmail account username. Does anyone have any help for a solution to this?

I don't have the 'User ID' field either. However, following the instructions given here, sending email still works. this is despite the 'From' field in the mutt sent mail folder claiming the email was sent from my local username and not my gmail username

---


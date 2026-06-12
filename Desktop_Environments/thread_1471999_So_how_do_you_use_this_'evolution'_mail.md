---
title: "So how do you use this 'evolution' mail"
date: 2010-05-04
forum: Desktop Environments
---

### Post by dE_logics on 2010-05-04
I want a list of accounts towards the mail area on the left...but that's not happening, instead I get 'on this computer...which is utterly crap, confusing and I wanna do away with it.

---

### Post by xDarkicex on 2010-05-04
Evolution is Easy to use, just add your account set it up like you would any other email forwarding  program.

---

### Post by Hambombj on 2010-05-04
I went straight to thunderbird when i installed ubuntu, but have switched to Evolution, was a bit of hassle setting up my email account (BT in the uk) but now it works fine, only issue I have is although it's set to play a sound on receipt of new mail, it doesn't!

But that's no problem.

as said above it is no more difficult to set up than any other I have used.

---

### Post by dE_logics on 2010-05-04
Actually I've never used an e-mail client.

but I want grouping of the email accounts by their name...that ain't happening.

Can someone post a screen shot?

Evolution is nicely integrated with the Ubuntu-desktop, so it will be a really good idea using it.

---

### Post by xDarkicex on 2010-05-04
As soon as I get ubuntu install on my main rig  *will post some shots if no one else has by then*

---

### Post by martijntje on 2010-05-04
If you get your mail in the 'On this computer' folder, that probably means that you are using POP3 to retrieve your mail and then remove it from the server.

The grouping of email accounts you are talking about happens automatically when you use IMAP to synchronize your email. I think this is what causes the confusion. There are a few things you can do:

1) Use IMAP. This is the easiest solution. You will be able to sync your mail on many computers and this will solve your problem. If your provider for one reason or another does not support IMAP, you can easily create a gmail account, tell it to retrieve mail from your POP3 account and then use IMAP to access this gmail account.

2) You can set up filters to sort your mail to different folders based on the email address it was sent to.

---

### Post by dE_logics on 2010-05-05
> **martijntje said:**
> If you get your mail in the 'On this computer' folder, that probably means that you are using POP3 to retrieve your mail and then remove it from the server.

The grouping of email accounts you are talking about happens automatically when you use IMAP to synchronize your email. I think this is what causes the confusion. There are a few things you can do:

1) Use IMAP. This is the easiest solution. You will be able to sync your mail on many computers and this will solve your problem. If your provider for one reason or another does not support IMAP, you can easily create a gmail account, tell it to retrieve mail from your POP3 account and then use IMAP to access this gmail account.

2) You can set up filters to sort your mail to different folders based on the email address it was sent to.

I thought gmail only worked with pop.

What about yahoo, hotmail, reddif?

---

### Post by martijntje on 2010-05-05
> **dE_logics said:**
> I thought gmail only worked with pop.

What about yahoo, hotmail, reddif?

GMail supports both.

---

### Post by dE_logics on 2010-05-05
I know yahoo and specially hotmail is complete crap...but is there anyway to set them up with evolution?

---

### Post by pricetech on 2010-05-20
Check out the fourth post on this thread:

[http://ubuntuforums.org/showthread.php?t=1468134]("http://ubuntuforums.org/showthread.php?t=1468134")

This is what worked for me.

---

### Post by dunbrokin on 2010-05-31
This is a cross post from Absolute Beginners. I am having a real problem accessing my email accounts using both Thunderbird and Evolution. I cannot send or receive using either client. I have checked and rechecked the settings (am using port 110 for incoming and 10025 for outgoing). If it were not for gmail I would be screwed as I cannot contact my clients. I was using TB in 9.10 with no problem until I upgraded to 10.04 yesterday. Any help much appreciated.

---

### Post by JustinR on 2010-06-01
> **Hambombj said:**
> I went straight to thunderbird when i installed ubuntu, but have switched to Evolution, was a bit of hassle setting up my email account (BT in the uk) but now it works fine, only issue I have is although it's set to play a sound on receipt of new mail, it doesn't!

But that's no problem.

as said above it is no more difficult to set up than any other I have used.

Hi! If you want to a play sound when evolution starts, go into Evolution:

Edit>Message Filters>Add

Under find items click "If any conditions are met"
Click sender and press "Match All"

Then click "Move to Folder" and press "Play Sound"
Then locate your sound file on the button to the right.

---


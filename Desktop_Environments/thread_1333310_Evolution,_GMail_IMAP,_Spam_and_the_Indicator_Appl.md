---
title: "Evolution, GMail IMAP, Spam and the Indicator Applet"
date: 2009-11-21
forum: Desktop Environments
---

### Post by ions on 2009-11-21
I am using GMail with IMAP and evolution. I have several directories set up for sorting messages as they arrive so I have Evolution set to display a notification when mail arrives in "any Folder" versus just my "inbox." The problem with this is the indicator applet lets me know when mail arrives in the spam folder thus rendering the indicator applet nearly useless.

Is there a way to either tell Evolution don't bother checking the spam folder on Gmail because I don't care what's in there and/or telling Evolution to alert me of mail in any other folder but spam?

---

### Post by ions on 2009-11-21
Really? Nobody else has this? Or nobody else has this and thinks it's a problem?

---

### Post by ions on 2009-11-23
I had searched previous to posting this but wading through the immense amount of unrelated and poorly titled threads made it a frustrating exercise. Which I put myself through once again and found [this](http://ubuntuforums.org/showthread.php?t=894776&highlight=evolution+spam+gmail+imap) which will hopefully work, just set it and no mail has arrived yet to test it.

---

### Post by ions on 2009-11-23
Still getting new mail notifications from the indicator applet when new spam arrives.

---

### Post by Noo 2 Ubuntoo on 2009-11-26
As I understand it (and I may be wrong) the mail notification will be linking to your Gmail(IMAP) account via info it downloaded from evolution when you first set up the mail notification.

If this is the case it will be looking at all subscribed folders in evolution including the Spam folder. I think you have to unsubscribe evolution from the spam folder, but I cannot see how to do this. Evolution seems to do an automated process when first set up to link to webmail, subscribing to any folders it detects on the IMAP server, with no provision to manually unsubscribe individual folders.

---

### Post by ions on 2009-11-27
In Evolution I have gone to Folders > Subscriptions and selected Gmail then unchecked the Spam box. No behaviour changed - Spam is downloaded and indicated as new mail with the box checked or unchecked. Under folder properties I have made sure that "Always check for new mail in this folder" is unchecked (something else that makes no difference to behaviour).

I am debating deleting the spam folder but I fear that will just cause spam to be left in my inbox instead of sorted somewhere where I needn't see it or be made aware of its existence which is of course the appropriate behaviour. 

Perhaps during the December break I will revert back to Thunderbird and a different panel indicator as this behaviour is completely unsatisfactory.

---

### Post by sgosnell on 2009-11-27
It would seem to me that your beef might be with the indicator applet.  Are there any option available for that?

---

### Post by ions on 2009-11-28
Actually I'd like Evolution not to bother downloading the spam, ignore it as Thunderbird does. But if I could get the indicator app not to show new spam that would be fine too. How?

---

### Post by sgosnell on 2009-11-28
Dunno.  It's not something I've ever worried about, thus never investigated.

---

### Post by ions on 2009-11-28
uh... thanks? 

Is there anybody else who IS using Evolution, GMail with IMAP and the indicator applet? Do you have this problem too or is it just me?

---

### Post by rockhopper on 2009-12-06
> **ions said:**
> In Evolution I have gone to Folders > Subscriptions and selected Gmail then unchecked the Spam box. No behaviour changed - Spam is downloaded and indicated as new mail with the box checked or unchecked. Under folder properties I have made sure that "Always check for new mail in this folder" is unchecked (something else that makes no difference to behaviour).


Apart from these steps, I have also unchecked "check for new mail in all folders" in the account-settings->receiving mail. Does that work for you?

---

### Post by ions on 2009-12-07
That would work but then I wouldn't be alerted for the email that goes into all my other folders, just the ones in the inbox. MOST of my mail gets sorted into other folders.

---

### Post by ions on 2009-12-13
Really?! I mean REALLY? I am the only person using the combination of GMAIL, IMAP and Evolution? Can't be. Unpossible. 

I should have some time later this week to move over (back) to Thunderbird and Lightning, this is just f'n ridiculous. Spam is not new mail. Evolution and the update notifier should know that. Not hard.

---

### Post by mister_playboy on 2009-12-13
> **ions said:**
> Really?! I mean REALLY? I am the only person using the combination of GMAIL, IMAP and Evolution? Can't be. Unpossible. 

I should have some time later this week to move over (back) to Thunderbird and Lightning, this is just f'n ridiculous. Spam is not new mail. Evolution and the update notifier should know that. Not hard.

Thunderbird is just far better than Evolution, IMO.  It ought to be the default for Ubuntu.

---

### Post by sgosnell on 2009-12-14
I use evolution, gmail imap, but I don't use the indicator applet, so I don't have the problem.

Thunderbird can't replace evolution, because it doesn't do nearly all that evolution does.  Thunderbird is fine for email, but evolution does much more than email.

---

### Post by ions on 2009-12-16
Thunderbird better not replace the amount of annoyance I'm getting with Evolution. Installing Tbird 3 tomorrow.

---

### Post by P3t3r on 2010-05-08
Just wondering, did this get any success?

---


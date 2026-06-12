---
title: "Conky rss"
date: 2009-01-15
forum: General Help
---

### Post by jonathanyates on 2009-01-15
Any reason with this might not work ?

EMAIL
${rss hXXps://jonathanaytesdotbiz:XXXXXX@gmail.google.com/gmail/feed/atom 1 item_titles 10}

I would like to display the unread emails in gMail and I thought that I could parse the rss atom feed via the RSS variable for CONKY. Would this never work as it is ATOM via RSS hence the output:

prss: Error reading RSS data


Is there a way to parse and atom feed into rss and then use this ?

Cheers

Jonathan
NEWBIE conky user but trying

---

### Post by jonathanyates on 2009-01-15
Found thisif it helps ?

Do you want to know when new mail has arrived in your Gmail account? Of course you do. One way to stay up to date is keeping a Gmail browser window open in the background (Gmail will display the number of unread messages in the window title).

If that's not quite your thing, Gmail's Atom feeds may be. You can add Gmail to your RSS feed reader (provided it supports feed authentication; many web-based aggregators like Bloglines do not) and find out about all unread mail — the subjects and senders as well as a bit of the message body, too — in a timely manner. You can even set up feeds that track specific Gmail labels.
Get Gmail Notifications (Even Per Label) in Your RSS Feed Reader

To get notified of new Gmail messages in your RSS news feed reader:

    * Launch your RSS feed reader.
    * Create a new channel.
    * Type "https://gmail.google.com/gmail/feed/atom" for the URL of the new feed.
    * Enter your Gmail user name ("sammy.sample") when prompted for a user name.
    * Use your Gmail password as the feed's password, too.
          o If that does not work, try using "https://[your Gmail user name]:*[your Gmail password]@gmail.google.com/*gmail/*feed/atom" (like "https://sammy.sample:passphrase@gmail.google.com/*gmail/*feed/*atom") for the URL. 

To get notifications for new messages in a Gmail label in your RSS feed reader:

    * Append the label to the "https://gmail.google.com/*gmail/*feed/*atom/" URL (note '/' at the end).
          o For example, a label called "todo" can be tracked using the URL "https://gmail.google.com/*gmail/*feed/*atom/*todo". 
    * Add the URL to your RSS feed reader as above.

---


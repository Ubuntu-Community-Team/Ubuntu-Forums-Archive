---
title: "Script to get my computer to read my email?"
date: 2009-05-15
forum: General Help
---

### Post by t0p on 2009-05-15
I've got this idea of sending commands to my computer via email.  So I want ubuntu to check my gmail account periodically, to look at the subject lines of new emails and then to "read" the body of an email to look for a command.  So, for instance, ubuntu looks out for emails with the subject line "command via email", then looks through the body of such an email to find the command.

Can someone please tell me how I can enable this functionality?  What scripting commands allow the computer to access emails?  I currently use evolution to manage my gmail accounts.  Would I be better off using a different email client, in connection with this project?

---

### Post by soro2005 on 2009-05-15
I guess that, rather than Evolution, you would set up a mailproxy/server that can relay your gmail imap account into your local mailbox. Perhaps, you can even filter it in gmail so that you don't produce a lot of clutter. I'm not sure how to go about it, but dovecot seems to be something to look into, and [this](http://sachachua.com/wp/2008/05/08/geek-how-to-use-offlineimap-and-the-dovecot-mail-server-to-read-your-gmail-in-emacs-efficiently/) might be a start.

Once you have it in your local mailbox, it shouldn't be difficult to trigger a script that reads the command and executes it. I don't know how to catch the event, but on my computer, gnubiff breaks loose heavens and hell everytime there's new mail in the mailbox. In the worst of cases, you could use a cronjob.

Make sure that others can't send commands to your computer :lolflag:

*Edit: Dovecot is nonsense, getmail would be much easier.*

---

### Post by soro2005 on 2009-05-15
Much better idea: You could find a commandline feed reader, set it up to periodically read the atom feed from your gmail inbox, and pipe the output into some script to parse and execute commands. That would be much leaner, and it should be easy to make sure that you only execute new commands.

---

### Post by soro2005 on 2009-05-15
Ok, I found this interesting. I've found out that you can use wget to read your gmail atom feed, like this:

```
wget -T 3 -t 1 -q --secure-protocol=TLSv1 --no-check-certificate --user=USERNAME --password=PASSWORD https://mail.google.com/mail/feed/atom -O -
```

You could filter this with sed for the string you want to execute, and run it every couple of minutes as a cron job.

You'd still have to find a way to execute each command only once, though.

---

### Post by HermanAB on 2009-05-15
Yes, fetchmail and procmail can do that.  Procmail is part of the fetchmail package.  Setting it up to do that isn't easy though.

---

### Post by t0p on 2009-05-15
> **soro2005 said:**
> Ok, I found this interesting. I've found out that you can use wget to read your gmail atom feed, like this:

```
wget -T 3 -t 1 -q --secure-protocol=TLSv1 --no-check-certificate --user=USERNAME --password=PASSWORD https://mail.google.com/mail/feed/atom -O -
```

You could filter this with sed for the string you want to execute, and run it every couple of minutes as a cron job.

You'd still have to find a way to execute each command only once, though.

Wow that's cool!  Cheers for the heads-up on using wget with the gmail feed, I think that's the way to go.  Now I gotta read up on sed.

---

### Post by t0p on 2009-05-15
Okay, I've looked at soro2005's suggestion about using wget and gmail's atom feed.

Thing is, I use soro2005's code snippet and I get just a list of new messages.  I need to open the emails and look at their contents.

If I use a gui aggregator (eg akregator) I get a list of recent emails, and I can see the contents by clicking on the "article" subject.  I need to know how to do this from the command-line.  I need ubuntu to fetch the list of new emails, look through the subject-lines to check for a particular subject, then open that mail and look for the command.  Can anyone tell me how I might do that?  Can someone point me in the direction of a HOWTO on this subject?

---

### Post by soro2005 on 2009-05-15
I think you'd need to:
1. Keep a file with the atom feed from the last run
2. Produce a file with the atom feed from the current run
3. Compare the two with diff, and only process the new parts. That's to prevent executing everything five times. The problem is that, as soon as the message is marked as "read" by gmail, it doesn't come with the feed any more, so that you make sure your diff returns only what is in the newer file, and not in the older one.
4. Once you have the new and relevant messages isolated, it should be easy to parse them for some secret keyword and execute it
5. Replace the file with the atom feed from the last run with the one from the current run

While this seems very feasible, the procmail solution is perhaps the more professional and extensible one.

Ps: I can perfectly see the beginning of the message body in the Atom feed. It's in the <summary></summary> tag

---

### Post by soro2005 on 2009-05-15
Just as a proof of concept. If you replace your username and password, and send yourself an email with the subject COMMAND, then this should output the beginning of the body of the email --> more than enough for some commands. You could easily execute it.
```
wget -T 3 -t 1 -q --secure-protocol=TLSv1 --no-check-certificate --user=USERNAME --password=PASSWORD https://mail.google.com/mail/feed/atom -O - | sed -n 'N;/<title>COMMAND<\/title>\n.*/p' | grep summary | sed 's/<summary>\(.*\)<\/summary>/\1/'
```
Again, this is just b/c I was bored and wanted to figure it out. The right tool to use is procmail. For this one here, you'd have to keep a rotating record of what you've already seen/executed.

---

### Post by t0p on 2009-05-16
> **soro2005 said:**
> 
Again, this is just b/c I was bored and wanted to figure it out. The right tool to use is procmail. For this one here, you'd have to keep a rotating record of what you've already seen/executed.

Thanks for the proof of concept.  Now I'll check out procmail.

---


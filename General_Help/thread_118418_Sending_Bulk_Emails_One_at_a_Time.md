---
title: "Sending Bulk Emails One at a Time"
date: 2006-01-17
forum: General Help
---

### Post by mlissner on 2006-01-17
Ok, this might not be the right forum, but...

I'm trying to send an email to about a hundred people, many of them old college friends. This creates two problems:
1. My alma mater, Pitzer College, will think this email is junk if more than a couple of my friends get it at a time.
2. My SMTP server will not let me send it to more than, say, 20 people at a time.

So the question is, does anybody know a way to create a list of email addresses that I want to send this to and then have Ubuntu send off a separate email to each of those people (so it looks like I only sent it to that one person)?

FYI, I thought Thunderbird might do it, but so far, alas.

Thanks in advance, I know the answer is out there.

-mike

---

### Post by sunny_nwho on 2006-01-17
try using the cc in thunderbird if u use bcc then the email addresses will not be disclosed....but on the other hand ur smtp might not allow u to send more than a prescribed limit....u must check with ur administrator

---

### Post by Horndog on 2006-01-17
Try a email service [from google]("http://www.google.com/search?hl=en&lr=&q=newsletter+broadcast+services&btnG=Search").

---

### Post by mlissner on 2006-01-17
Yeah, I was doing BCC's on it anyway, to keep my friends from knowing each other :), but I still had the problem with my ISP.

As for using a broadcasting service, that's an idea, and one I had found, but I don't like it. Surely, those people are just running Linux anyway right? They don't have anything we don't have access to...

I guess the means is also the ends in this project; I don't only want to get it done, I want to know how to do it.

Any other ideas out there?

-mike

---

### Post by nocturn on 2006-01-17
If you want to get into the command line, or perl, you can do it easy

---

### Post by Horndog on 2006-01-17
By the way if your thinking of a mail server then you should know that most home isp accounts have the smtp(out going) port blocked (25 I think). I have an account with [https://www.dyndns.com]("https://www.dyndns.com") and they offer for a fee an outgoing smtp service with a domain name of your choosing, again for a fee.

---

### Post by mlissner on 2006-01-17
I'd love to do it command line or perl, but I don't know perl at all, and I'm somewhat new with the command line. 

I know about port 25...that one's annoying as all hell to figure out the first time. I was so pissed when I called SBC, and the amount of time it takes the bastards to fix it?!

Anyway, command line or perl...any takers?

---

### Post by nocturn on 2006-01-18
You can open an SMTP socket in perl with this code.  You need to put your mail in @message and we need to add al loop (get the addresses from a list).

```

#!/usr/bin/perl
use Net::SMTP;

my $smtphost = "smtp.yourisp.com";

# Send the mail
# Set this variable to your smtp server name

# Create a new SMTP object
$smtp = Net::SMTP->new($smtphost, Debug => 0);

# If you can't connect, don't proceed with the rest of the script
die "Couldn't connect to server" unless $smtp;

# Initiate the mail transaction
# Your "real" email address
my $MailFrom = "root\@$dnsdomain";

# Recipient's "real" email address
my $MailTo = "$myuser\@$dnsdomain";

$smtp->mail( $MailFrom );
$smtp->to( $MailTo );

# Start the mail
$smtp->data();

# Send the header
# This address will appear in the message
$smtp->datasend("To:  $myuser\@$dnsdomain\n");

# So will this one
$smtp->datasend("From:  $MailFrom\n");
$smtp->datasend("Subject: $subject\n");
$smtp->datasend("\n");

# Send the body.
$smtp->datasend("@message\n\n");

# Send the termination string
$smtp->dataend();

# Close the connection
$smtp->quit();


```

This is just an example, it needs some variables etc to work.

---

### Post by nocturn on 2006-01-18
If your local postfix can send to external addresses (try your own first), this will do it on the command line (if not, you need to specify a relayhost to your ISP).

Put all addresses in a file called addresses.txt (one per line), create the message as message.txt.

```

for i in `cat addresses.txt`; do cat message.txt | mail -s "my subject" $i; sleep 300; done

```

The sleeptime is in seconds, so 300 means to wait 5 minutes between messages.  You can adjust to your own need.

---

### Post by lamego on 2006-01-18
A lot of SMTPs now check for dynamic IPs on dns black lists, to use the script from nocturn (which should work fine) I strongly sguest you to change your postfix configuration to relay on your ISP SMTP server.

---

### Post by mlissner on 2006-01-20
I liked the command line technnique - It looked solid, but it doesn't seem to work for me. I get the command not found error for mail:
bash: mail: command not found.

Too bad too. I want this to work. Apt-getting mail didn't work either. Any suggestions?

Oh, and I'm really not sure at all what changing the postfix configuration means (sigh).

---

### Post by mlissner on 2006-01-20
Sorry. Disregard this post. My mistake...I'd delete it if I could, but apparently there's no way to do that.

Side note: Is this webpage as confusing to other people as it is to me?

---

### Post by mlissner on 2006-01-24
OK, I've attempted more progress on this, but am still failing. I tried to install pico, failed for some reason, installed Mutt, realized that postix is really complex, and failed at making any real settings in there....

But...I still have the same problem: the mail command in that earlier prompt still doesn't work. What package would it take, or what other ideas are out there?

We're close, but not there yet.

---

### Post by nocturn on 2006-01-27
You'll need to install the package mailx to get the mail command.

And add the line :
relayhost = your.isp.mail

to /etc/postfix/main.cf

Maybe your ISP may still reject the mails based on the From header.

---

### Post by mlissner on 2006-01-28
OK, we're close. Mailx seems to work, but now the problem is configuring postfix. I entered the line you said, and now I think I need to enter my SMTP username and password into it so I can send email through it. I read it's documentation, and looked around on the web a bit, but to no avail (this is somewhat over my head, so I'm trying just to stay afloat now).

So, is my theory about needing the smtp username and password correct? How do we put them in?

Thanks again.

---

### Post by dcstar on 2006-01-28
[QUOTE=Horndog]Try a email service [from google]("http://www.google.com/search?hl=en&lr=&q=newsletter+broadcast+services&btnG=Search").[/QUOTE]
Or set up a [Yahoo Group]("http://groups.yahoo.com/") with all the e-mail addresses in it as members, then you send one e-mail to the group and it is distributed to all members.

---

### Post by mlissner on 2006-01-28
That's not what I'm after. I want to be able to do this whenever I want without having to deal with a third party and everything that comes with them. Plus, if we get this down in the forums, maybe other people will find it useful. 

I'm convinced we're nearly there.

Thanks though. It's not a bad thought.

---

### Post by nocturn on 2006-01-30
You can check if you use authentication normally in the settings of your mail client (evolution?)

I cannot find an option to tell this to postfix.

What error do you get from postfix about the relaying?

---

### Post by mlissner on 2006-01-30
Thanks again for your time. I do usually use authentication with my ISP. If it didn't require authentication, what would be stopping me from using your SMTP to send all these messages?

Here's the bulk of the message Postfix is giving me. Thanks for all the help:

From: [email]MAILER-DAEMON@sbcglobal.yahoo.com[/email] (Mail Delivery System)
Subject: Undelivered Mail Returned to Sender
To: [email]root@sbcglobal.yahoo.com[/email]
MIME-Version: 1.0
Content-Type: multipart/report; report-type=delivery-status;
        boundary="8CB3F248313.1138467168/localhost.localdomain"

This is a MIME-encapsulated message.

--8CB3F248313.1138467168/localhost.localdomain
Content-Description: Notification
Content-Type: text/plain

This is the Postfix program at host localhost.localdomain.

I'm sorry to have to inform you that your message could not
be delivered to one or more recipients. It's attached below.

For further assistance, please send mail to <postmaster>

If you do so, please include this problem report. You can
delete your own text from the attached returned message.

                        The Postfix program

<mlissner@aidshike.org>: host smtp.sbc.mail.yahoo4.akadns.net[68.142.198.11]
    said: 530 authentication required - for help go to
    [http://help.yahoo.com/help/us/sbc/dsl/mail/pop/pop-11.html](http://help.yahoo.com/help/us/sbc/dsl/mail/pop/pop-11.html) (in reply to
    MAIL FROM command)

--8CB3F248313.1138467168/localhost.localdomain
Content-Description: Delivery report
Content-Type: message/delivery-status

Reporting-MTA: dns; localhost.localdomain
X-Postfix-Queue-ID: 8CB3F248313
X-Postfix-Sender: rfc822; [email]root@sbcglobal.yahoo.com[/email]

---

### Post by nocturn on 2006-01-31
Most SMTP servers do not authenticate with a password.
My ISP limits SMTP access to its own IP range, it checks the sender address and has rate limiting.  

But, I found something about using authentication with postfix:
[http://www.opengroupware.org/en/users/docs/snippets/Mail/postfixauth.html](http://www.opengroupware.org/en/users/docs/snippets/Mail/postfixauth.html)

---

### Post by funkydan2 on 2006-01-31
My Ubuntu laptop is away getting fixed, so I might be wrong about this.

Why don't you do an email merge in OpenOffice.org Writer?  You just need to wip up a really simple database (or CSV file) with their Name and Email address.  Then go into the "Mail Merge Wizard" and select "Email Merge".

You'll need to put in your SMTP server settings in Tools->Options->OpenOffice.org Writer->Mail Merge E-mail

Sending HTML formatted emails is as easy as any other mail merge (i.e. not completely bug free yet in OO.org)

Daniel

---

### Post by nocturn on 2006-01-31
[QUOTE=funkydan2]My Ubuntu laptop is away getting fixed, so I might be wrong about this.

Why don't you do an email merge in OpenOffice.org Writer?  You just need to [/QUOTE]

Because that will send all the messages in a single timeframe, which probably isn't allowed by the ISP (rate limiting).

---

### Post by mlissner on 2006-02-01
Yes. Nocturn again speaketh the truth. The idea here is to foil the over-eager spam filters of my friends, and make it seem as if the email has gone ONLY to them even from the spam filter's perspective. 

In the past, when sending mail to multiple people at my alma mater, the filter flagged them as spam, and didn't let them through...

---

### Post by nocturn on 2006-02-01
[QUOTE=mlissner]Yes. Nocturn again speaketh the truth. The idea here is to foil the over-eager spam filters of my friends, and make it seem as if the email has gone ONLY to them even from the spam filter's perspective. 

In the past, when sending mail to multiple people at my alma mater, the filter flagged them as spam, and didn't let them through...[/QUOTE]

If it is only the spam filter on the recipient end, the OO solution will work too.  
If your ISP does rate limiting (mine does), it will still fail.

---

### Post by Stormspace on 2006-02-01
[QUOTE=mlissner]Yeah, I was doing BCC's on it anyway, to keep my friends from knowing each other :), but I still had the problem with my ISP.

As for using a broadcasting service, that's an idea, and one I had found, but I don't like it. Surely, those people are just running Linux anyway right? They don't have anything we don't have access to...

I guess the means is also the ends in this project; I don't only want to get it done, I want to know how to do it.

Any other ideas out there?

-mike[/QUOTE]

I wrote a VBA script a couple of years ago that would iterate through a table in access and send one off's to a group using the mapi functions in windows.

It worked very well. I suppose you could also run it from Word or Excel as well, you just need to code it.

---

### Post by nocturn on 2006-02-02
[QUOTE=Stormspace]
It worked very well. I suppose you could also run it from Word or Excel as well, you just need to code it.[/QUOTE]

Yes, but these are Linux forums, and he's asking for a solution to do this on Linux.  So, an OpenOffice macro, shell script or perl may do the trick.

---

### Post by mlissner on 2006-02-07
Ok, I tried the OpenOffice merge thing, and it worked like a charm...for the first 25 people. Then it failed and wouldn't continue. Yes, it appears we have an ISP rate limit on our hands folks. 

Now I have sent it to 25 seemingly random people on the list, what's the next grand idea? Is there an easy way to build a timer into the email merge thing?

---


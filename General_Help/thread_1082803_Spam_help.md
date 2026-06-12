---
title: "Spam help ?"
date: 2009-02-28
forum: General Help
---

### Post by asearle on 2009-02-28
Hallo Everyone, 

I'm sorry to post a message that is a bit 'off subject' but you guys have always given me good Ubuntu advice in the past and so I am really hoping that someone out there has a tip for me or can give me a link to a site where they might be able to help.

With my e-mail I handle spam that I receive with a spam filter.  That works more or less OK.  My e-mail is managed by my service provider with me being able to some options (e.g. password).

However, over the past few months, I have started to receive spam from my own e-mail address:  This is someone else sending spam via my address (apparently).

I changed my password and contacted my service provider but they say that there is nothing they can do about it and that I should trace back and contact the service provider which forwarded the mail.  However, each time the transit ISP seems to be different and so that would be a wild goose chase.

Anyway, I really hope that somone out there can help me because I am afraid that others will be receiving these spam mails and that my address will start appearing on spam black lists.

Any help would be most gratefully received.

Regards,
Alan Searle

---

### Post by Pringles on 2009-02-28
They are most likely not sending spam WITH your email address.

They are most likely just setting the "From" field to the same as the "To" field in their spam code.

If you start getting a bunch of "Failed to send to this address" messages then they are using your address, but that is usually just temporary.

---

### Post by s.fox on 2009-02-28
I don't think they are sending from your email address.   You might want to try looking at your Sent folder just to check.

---

### Post by asearle on 2009-02-28
> They are most likely not sending spam WITH your email address.

OK, thanks.

> They are most likely just setting the "From" field to the same 
> as the "To" field in their spam code.

Ah, ha, I see.  So I am the only one receiving these mails from my own address.  That's a relief!

> If you start getting a bunch of "Failed to send to this 
> address" messages then they are using your address, but that 
> is usually just temporary.

Yes, you're absolutely right:  There was a phase where I got bombarded with "undeliverable" messages but this has stopped now.

Many thanks:  You have removed a big worry that I was having.  Now I know that this is just a trick to get past my spam filter and they are not really using my address to send spam out into the 'big wide world'.

Regards and big thanks,
Alan Searle

---

### Post by oldos2er on 2009-02-28
In order to determine where the spam came from, we'd need to see the headers.

---

### Post by asearle on 2009-02-28
Hi guys,

Below is one of the headers.  VTX.CH is my service provider.

My e-mail address is [email]asearle@xxx.com[/email]  (with xxx replacing my real domain name).

However, I don't think this is worth pursuing as, as one of the other contributers mentioned, I don't think they are using my e-mail for widespread spamming but rather just as a method to get past my spam filter.

Many, many thanks for your help.

Regards,
Alan


Header:

X-Account-Key: account2
X-UIDL: UID21784-1195381322
X-Mozilla-Status: 0001
X-Mozilla-Status2: 00000000
X-Mozilla-Keys:                                                                                 
Return-Path: <asearle@xxx.com>
X-Original-To: [email]asearle@xxx.com[/email]
Delivered-To: [email]asearle@xxx.com[/email]
Received: from mx-03.vtx.ch (mx-03.vtx.ch [212.147.0.116])
	by pop-pro-04.vtx.ch (VTX Services SA) with ESMTP id AAD1C10F39A
	for <asearle@xxx.com>; Sat, 28 Feb 2009 08:49:41 +0100 (CET)
Received: from 3isolution.com (unknown [203.169.53.82])
	by mx-03.vtx.ch (VTX Services SA) with SMTP id F33C1117C50
	for <asearle@xxx.com>; Sat, 28 Feb 2009 08:49:37 +0100 (CET)
To: <asearle@xxx.com>
Subject: DataArt Newsletters
From: <asearle@xxx.com>
MIME-Version: 1.0
Importance: High
Content-Type: text/html
Message-Id: <20090228074939.F33C1117C50@mx-03.vtx.ch>
Date: Sat, 28 Feb 2009 08:49:37 +0100 (CET)****

---

### Post by brian_p on 2009-02-28
> **asearle said:**
> 
                                                                          
Return-Path: <asearle@xxx.com>

The envelope From. Can be forged.

> Received: from mx-03.vtx.ch (mx-03.vtx.ch [212.147.0.116])
	by pop-pro-04.vtx.ch (VTX Services SA) with ESMTP id AAD1C10F39A
	for <asearle@xxx.com>; Sat, 28 Feb 2009 08:49:41 +0100 (CET)

Your ISP has put the mail in your mailbox on pop-pro-04.vtx.ch

> Received: from 3isolution.com (unknown [203.169.53.82])
	by mx-03.vtx.ch (VTX Services SA) with SMTP id F33C1117C50
	for <asearle@xxx.com>; Sat, 28 Feb 2009 08:49:37 +0100 (CET)

Your ISP received a mail with an envelope To of <asearle@xxx.com>

> To: <asearle@xxx.com>

This is the To: header (which is not the same as the envelope To). It can be forged.

> Message-Id: <20090228074939.F33C1117C50@mx-03.vtx.ch>

Added by your ISP because the original mail did not have one.

About the only thing you can conclude from this is that you received a mail form a doubtful source. You cannot deduce other mails with <asearle@xxx.com> in the From: header or envelope from have not been sent.

---

### Post by emarkay on 2009-02-28
I have been getting this now a lot too.  I just delete any eails from "me" - I keep my ISP email pretty "secure" and know what emails I get - I haven't even bothered to look into it because I presume that some "Windows Zombie" PC has my valid email address and us using it as a "From" ID....

---


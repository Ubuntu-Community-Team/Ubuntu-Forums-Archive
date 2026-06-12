---
title: "[SOLVED] debtags cron job failing"
date: 2008-12-13
forum: General Help
---

### Post by ezramorris on 2008-12-13
Hi,
I get this internal mail from cron every few days. Any idea what it means and what I can do about it?

Thanks.

> From root@ezra-laptop Fri Oct 24 00:44:55 2008
Return-path: <root@ezra-laptop>
Envelope-to: root@ezra-laptop
Delivery-date: Fri, 24 Oct 2008 00:44:55 +0100
Received: from root by localhost with local (Exim 4.69)
        (envelope-from <root@ezra-laptop>)
        id 1Kt9rK-0002NY-Vn
        for root@ezra-laptop; Fri, 24 Oct 2008 00:44:55 +0100
From: Anacron <root@ezra-laptop>
To: root@ezra-laptop
Subject: Anacron job 'cron.daily' on ezra-laptop
Message-Id: <E1Kt9rK-0002NY-Vn@localhost>
Date: Fri, 24 Oct 2008 00:44:54 +0100
Status: RO

/etc/cron.daily/debtags:
/etc/cron.daily/debtags: 4: debtags: not found
run-parts: /etc/cron.daily/debtags exited with return code 127

[COLOR="Red"]Edit: [/COLOR]just realised debtags wasn't installed. Just installed it, but will post back if I still have problems.

---


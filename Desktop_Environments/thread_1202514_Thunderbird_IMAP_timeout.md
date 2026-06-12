---
title: "Thunderbird IMAP timeout"
date: 2009-07-02
forum: Desktop Environments
---

### Post by herda05 on 2009-07-02
I've got a new install of Thunderbird that I'm attempting to setup. I followed the [guide listed here]("http://mail.google.com/support/bin/answer.py?hl=en&answer=77662") to setup thunderbird with IMAP.

However, I get a timeout every time I go to connect to my email. I enabled IMAP in gmail's config. It's not a network issue either because I can ping imap.gmail.com, and I can telnet to port 993 form the command line. I used wireshark to sniff the packets, so I see the packet going out to imap.gmail.com to port 993. It appears to be some kind of application issue with Thunderbird, maybe the config?

Has anyone else had problems connecting to gmail IMAP with Tunderbird. Google wasn't helpful, so I can't see why this isn't easy...

thanks,
Dan H

---

### Post by herda05 on 2009-07-02
Found the issue. I was setting TLS instead of SSL.

Also if you check the "Use secure authentication" when you attempt to connect, you will receive an error stating that the server does this.

Dan H.

---


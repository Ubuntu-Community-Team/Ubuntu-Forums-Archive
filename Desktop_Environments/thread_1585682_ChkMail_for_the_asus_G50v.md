---
title: "ChkMail for the asus G50v"
date: 2010-09-30
forum: Desktop Environments
---

### Post by kkaldroma on 2010-09-30
After I moved from windows to ubuntu I wanted my Chkmail / oled to work with my Asus G50v.

The OLED screen was easily fixed with the [Asusg50oled]("http://asusg50oled.sourceforge.net/") bits found at the link and I wrote a quick and dirty script to make it work in Ubuntu.

This is setup to use Gmail but it can be adapted with some googlefu.
I hope this helps some other people that are in my position.

```

#! /bin/bash

USER=[your account name without the @ gmail.com]
PASS=[Your email password]

COUNT=$(wget --secure-protocol=TLSv1 --timeout=3 -t 1 -q -O - https://$USER:$PASS@mail.google.com/mail/feed/atom | grep "fullcount" | cut -d '>' -f 2 | cut -d '<' -f1)

if [[ $COUNT > 0 ]]; then
FROM=$(wget --secure-protocol=TLSv1 --timeout=3 -t 1 -q -O - https://$USER:$PASS@mail.google.com/mail/feed/atom | grep "email" | cut -d '>' -f 2 | cut -d '<' -f1)
SUBJECT=$(wget --secure-protocol=TLSv1 --timeout=3 -t 1 -q -O - https://$USER:$PASS@mail.google.com/mail/feed/atom | grep "title" | grep -v "Gmail" | cut -d '>' -f 2 | cut -d '<' -f1)
NAME=$(wget --secure-protocol=TLSv1 --timeout=3 -t 1 -q -O - https://$USER:$PASS@mail.google.com/mail/feed/atom | grep "name" | cut -d '>' -f 2 | cut -d '<' -f1)

cd /opt/asusg50oled/utils/

./notify.sh "<$FROM> $NAME"
./notify.sh "$SUBJECT"

fi


```Save this as you would any bash script..
     put it in /usr/local/bin/
     sudo chmod +x [whatever you called the script, I called it Chkmai]


then have it check your mail every minute using crontab
```

# m h  dom mon dow   command

* * * * * /usr/local/bin/Chkmail

```Done

---


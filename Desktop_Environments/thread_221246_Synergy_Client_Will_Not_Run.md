---
title: "Synergy Client Will Not Run"
date: 2006-07-22
forum: Desktop Environments
---

### Post by mooreted on 2006-07-22
Just installed Ubuntu and wanted to get Synergy desktop sharing working. When I try to run the client I get this error:

"Cannot execute binary file"

How can I get Syngery running?

Yes, I Googled it.

Yes, I read the help files.

Yes, I read the Readme file.

---

### Post by roostishaw on 2006-07-22
Since you havn't told us what you've tried yet, I can only suggest what I'm finding on google...

[http://www.google.com/search?hl=en&q=Synergy+ubuntu&btnG=Google+Search](http://www.google.com/search?hl=en&q=Synergy+ubuntu&btnG=Google+Search)

--> [https://help.ubuntu.com/community/SynergyHowto](https://help.ubuntu.com/community/SynergyHowto)

--> [http://philisoft.com/blog/install-latest-synergy-on-ubuntu/](http://philisoft.com/blog/install-latest-synergy-on-ubuntu/)

Tell me how it goes...

EDIT: Did you make it executable?
```

chmod +x /home/you/synergy.bin

```

---

### Post by mooreted on 2006-07-23
Thanks. I got it to work my installing thorough apt-get. I guess the binary provided my Sourceforge does not work in Ubuntu.

---


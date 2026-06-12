---
title: "nullmailer won't work.... Help."
date: 2009-04-14
forum: General Help
---

### Post by gbxfan on 2009-04-14
I have installed nullmailer 1.04-1 and as far as I can see with ps -ef its running:

mail      4420     1  0 16:03 ?        00:00:00 /usr/sbin/nullmailer-send -d

The main reason I got this was to use the command prompt to email out. I found examples of using nullmailer from the command 
```

mail -s "test" dale.smith@sbcglobal.net
whatever
[enter]
.[enter]
 and this doesn't work and I get the following error:

root@mpt1a02:/etc/nullmailer# mail -s "test" dale.smith@sbcglobal.net
The program 'mail' can be found in the following packages:
 * heirloom-mailx
 * mailutils
Try: apt-get install <selected package>
bash: mail: command not found

``` 

I have placed my smtp server hostname and ip information in the /etc/nullmailer/remotes file with a space at the end and smtp. Is there anything else I need to do? This is supposed to be easy from what all the sites say so I must be missing something.

Please give me some examples of how to use this from the command prompt.

Thanks for any help! Dale

---


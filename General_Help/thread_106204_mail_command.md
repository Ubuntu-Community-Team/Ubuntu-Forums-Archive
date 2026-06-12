---
title: "mail command"
date: 2005-12-20
forum: General Help
---

### Post by kirsche on 2005-12-20
Hello,

I'm trying to send a mail from the command line via the mail command (mailx package). I need to specify the dst/relay smtp server.
I couldn't finf the switch/parameter so far...
Does anyone have a hint for me?

Thanks

---

### Post by mcmuffy on 2005-12-20
In a console if you type 'man' followed by the command you are interested in it should give you information on the switches.

---

### Post by kirsche on 2005-12-20
I've tried man mail, tried help as well:
kirsche@bulmers:~$ mail --help
mail: invalid option -- -
usage: mail [-eIinv] [-a header] [-b bcc-addr] [-c cc-addr] [-s subject]
            to-addr [...] [-- sendmail-options [...]]
       mail [-eIiNnv] -f [name]
       mail [-eIiNnv] [-u user]
kirsche@bulmers:~$

The sendmail option for a relay host would be DS, but how can I use this with the mail command? I don't want/can't change the relay host in general.

---


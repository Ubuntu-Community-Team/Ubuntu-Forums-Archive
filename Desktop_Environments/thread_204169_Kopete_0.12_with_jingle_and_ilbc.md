---
title: "Kopete 0.12 with jingle and ilbc"
date: 2006-06-26
forum: Desktop Environments
---

### Post by Meck1982 on 2006-06-26
Hi all!
I have been successful in compiling kopete 0.12 with jingle support on kubuntu dapper and I am actually able to do audio chats with google talk users. But I think the sound quality isn't that good than in skype.
So I am asking myself if this could be improved by compiling kopete with iLBC support...

I already googled, got the sources from [http://simon.morlat.free.fr/download/1.2.x/source]("http://simon.morlat.free.fr/download/1.2.x/source")
and compiled and installed the lib by doing

$ ./configure
$ make
$ sudo checkinstall

But now when configuring kopete one more time the result is always:

Supported Jabber Jingle voice Codecs for Kopete:
Speex: yes
iLBC: no
MULAW: yes

Which means that iLBC has not been found by the configure script.

Any suggestions?

---


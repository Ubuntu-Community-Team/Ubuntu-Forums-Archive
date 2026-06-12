---
title: "Seeking a pop3 mail utility"
date: 2009-06-02
forum: General Help
---

### Post by graham bowers on 2009-06-02
In the bad old days of windoze I used to run a mail utility that accessed my pop3 mail server and gave me the opportunity to delete messages on the server. My reason for doing this was so that spam would not be delivered - and the hope that non delivered messages would get me off some lists.
Does such a utility exist for ubuntu please?
Graham

---

### Post by Greenwidth on 2009-06-02
Not sure if its what you mean exactly but you could telnet your mail server and delete messages without downloading them with Evolution or whatever:

```
telnet <yourmail.server> 110

user <your.username>

pass <your.password>

list - list messages

retr <number> - get selected message

dele <number> - delete selected message

quit - leave
```

NB - Type carefully, the keystrokes are sent as you type so no delete

---

### Post by dandnsmith on 2009-06-02
I think you can also do it with Thunderbird, but haven't looked at it for a while as I use a different reader client.

You can certainly decide how long to leave emails on the server, download headers only, delete from server stuff you've marked to delete locally.

---

### Post by brian_p on 2009-06-02
> **graham bowers said:**
> In the bad old days of windoze I used to run a mail utility that accessed my pop3 mail server and gave me the opportunity to delete messages on the server. My reason for doing this was so that spam would not be delivered - and the hope that non delivered messages would get me off some lists.

This is a vain hope - the mail has already been delivered to your mailbox.

> Does such a utility exist for ubuntu please?

It depends on the mail client you use. Mine (mutt) is capable of doing it. I don't because it is time consuming and better automated by the mailfilter package. If you do not mind learning a little bit about regular expressions you will find it very effective.

---

### Post by ellgor on 2009-06-02
Hi,

Take a look at kmail, it has the feature you request.

Regards, Ellgor.

---

### Post by RobHJ on 2009-06-28
In the Windows and PPC world there is a utility called nPOP that does what you’re looking for.
[http://www.nakka.com/soft/npop/index_eng.html](http://www.nakka.com/soft/npop/index_eng.html)

Source is available if you wanted to have a hack at it!

I haven’t found a Linux equivalent yet.

Rob

---


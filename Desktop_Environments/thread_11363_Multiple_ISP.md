---
title: "Multiple ISP"
date: 2005-01-16
forum: Desktop Environments
---

### Post by Kaddo on 2005-01-16
Is it possible to connect to more than one provider?
I'm on dialup and with two different accounts.
I managed to create a connection to one and it's working just fine.
Then, I did it for the second, but now I don't know how to run it, nor how to toggle between the two.
Any helpful hints will be appreciated.

---

### Post by zenwhen on 2005-01-16
```
zenwhen@sunball:~ $ pon -h
Usage: pon [OPTIONS] [provider] [arguments]
  -q|--quick           pppd hangs up after all ip-up scripts are run

If pon is invoked without arguments, /etc/ppp/ppp_on_boot file will berun, presuming it exists and is executable. Otherwise, a PPP connectionwill be started using settings from /etc/ppp/peers/provider.
If you specify one argument, a PPP connection will be started using
settings from the appropriate file in the /etc/ppp/peers/ directory, and
any additional arguments supplied will be passed as extra arguments topppd.
``` 

Basically, you add the name of the second connection after the pon command.

---

### Post by Kaddo on 2005-01-16
Basically, you add the name of the second connection after the pon command.[/QUOTE]

I did that.
And then what?

---

### Post by jobezone on 2005-01-16
In other words, by running pppconfig with sudo, you can create more than one conection.
You can then start the conection you want by running 
pon <name of the connection>

.

---


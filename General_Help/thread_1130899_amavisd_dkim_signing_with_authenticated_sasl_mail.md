---
title: "amavisd dkim signing with authenticated sasl mail"
date: 2009-04-20
forum: General Help
---

### Post by incredible_sulk on 2009-04-20
Hi,

I've hit a brick wall configuring amavisd-new to dkim sign sasl authenticated emails. The official documentation refers to authenticated signing, but being something of a newbie I can't make head nor tail of it:

[http://www.ijs.si/software/amavisd/amavisd-new-docs.html#dkim-impatient](http://www.ijs.si/software/amavisd/amavisd-new-docs.html#dkim-impatient)

So, at the moment I only have internal mail signing, like the example below:

```
  $enable_dkim_verification = 1;
  $enable_dkim_signing = 1;
  dkim_key('example.com', 'foo', '/var/db/dkim/example-foo.key.pem');
  @dkim_signature_options_bysender_maps = (
    { '.' => { ttl => 21*24*3600, c => 'relaxed/simple' } } );
  @mynetworks = qw(0.0.0.0/8 127.0.0.0/8 10.0.0.0/8 172.16.0.0/12
                   192.168.0.0/16);  # list your internal networks
```

All I need is a very simple setup, a personal mail server with a few domains the users which are all trusted, but want to be able to have authenticated users send dkim signed mail.

Cheers,
David

---


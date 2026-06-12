---
title: "Environment Variable through Apache2"
date: 2011-02-11
forum: Desktop Environments
---

### Post by dorivard on 2011-02-11
Hi everyone,

I'm looking for any idea why I can't passed to apache a variable define in /etc/profile.

Here is what I am trying to set:

I have a django application that I deploy through Apache/Passenger (modrails) through the WGSI interface.

In my settings.py I am using this python command :
ENVIRONMENT = os.getenv('ENV', 'PROD')
so if and ENVIRONMENT variable is not define it goes to the production settings by default.

That way I can manage which DB I connect to and activate debugging tools.

It is working in production because it is the default values, it's when I am on the DEV server that I can't get the environment variable to work.

So here is some test I did:

1) put into /etc/profile -> 
ENV='DEV'
export ENV

2) under /etc/profile.d/environment.sh -> 
#!/bin/sh
ENV='DEV'
export ENV

3) in my virtual host config file -> 
PassEnv ENV

4) still in my virtual host config file -> 
SetEnv ENV DEV

5) passenger require a passenger_wgsi.py to register your application if I force in this file 
os.environ['ENV'] = 'DEV' this gone a work but I am not able to do this

ENVIRONMENT = os.getenv('ENV', 'PROD')
os.environ['ENV'] = ENVIRONMENT

Any idea why?
thank you!

---


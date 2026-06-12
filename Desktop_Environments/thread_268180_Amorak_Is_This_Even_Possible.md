---
title: "Amorak: Is This Even Possible"
date: 2006-09-29
forum: Desktop Environments
---

### Post by Mark76 on 2006-09-29
I know you can set programmes to open automatically on start up, but I'd also like it to start playing a radio station when it does.

Can that be done?

---

### Post by mitch.c on 2006-09-29
> **Mark76 said:**
> I know you can set programmes to open automatically on start up, but I'd also like it to start playing a radio station when it does.

Can that be done?

Try this:
```
# Replace url with actual url for radio stream
amarok -p url
```

---

### Post by Mark76 on 2006-09-29
I take it this

> # Replace url with actual url for radio stream

part is redundant

---

### Post by Mark76 on 2006-09-29
Well that works when you type it into the terminal, but it doesn't get the player going on reboot/start up.  I tried it twice, once with Amarok added to start up programs and once with it not added.

So, I guess the answer must be no

---

### Post by mitch.c on 2006-09-29
> **Mark76 said:**
> Well that works when you type it into the terminal, but it doesn't get the player going on reboot/start up.  I tried it twice, once with Amarok added to start up programs and once with it not added.

So, I guess the answer must be no

Worked for me. It's a little clumsy trying to start quickly, so I created a script with a small delay, and it worked perfectly

Create a script called startamarok.sh
```
#!/bin/bash
sleep 15 && amarok -p $1
```

Put startamarok.sh in your path and set executable:
```
sudo chmod 755 startamarok.sh && mv startamarok.sh /usr/bin/
```

Add startamarok.sh to Startup Programs with url, for example:
```
/usr/bin/startamarok.sh http://68.165.71.58:18000
```

---


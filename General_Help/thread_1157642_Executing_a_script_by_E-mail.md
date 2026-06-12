---
title: "Executing a script by E-mail"
date: 2009-05-12
forum: General Help
---

### Post by drumfire420 on 2009-05-12
I'm really hoping someone here can help me.  I'm attempting to setup a personal server on my computer, I have the server stuff configured like I want.
The problem is I do not have a static IP
I also thought it would be cool if i could get my IP from my cell phone by text message.  

My idea became this:
send test message from cellphone to some email address of mine
computer receives email
computer runs script
script gets current ip
script sends email (with current ip) to SMS gateway for phone

I got the sms gateways from good old wikipedia
[List of carriers providing Email or Web to SMS ]("http://en.wikipedia.org/wiki/List_of_carriers_providing_Email_or_Web_to_SMS")

I have the script to get my WAN IP from my DD-WRT router, and send me an email with my IP
```
wget -q http://(IP OF ROUTER)/ --output-document="-" | grep ipinfo | cut -f 2 -d";" | cut -f 1 -d"<" | sendEmail -f "("FROM" EMAIL ADDRESS)" -t "(MY CELLPHONE'S EMAIL ADDRESS)" -u "Current IP" -s "(EMAIL SMTP SERVER)" -o tls=yes username="(EMAIL USERNAME)" password="(EMAIL PASSWORD)"
```
 (It works, but if you have any ideas on how to make it better I'm open to suggestions)

So, if any of the gurus here know how to execute a script from an email, this would be a really cool solution :P
Thanks

---

### Post by gradysghost on 2009-05-12
I highly recommend checking out these guys: [http://www.dyndns.com/](http://www.dyndns.com/) -- You can get a DNS address that follows the path to your dynamic IP, and it's completely free of charge.  Some basic port forwarding for SSH will give you access to your computer from virtually anywhere.  Using this method, I am able to get direct terminal access to my server from my cell phone.

In addition to that, you can use the -x flag on the ssh command to forward the X server over to whatever you're running, provided there's an X server on it, and get full GUI-based apps running remotely.  It's a fantastic system (albeit a little bit slow), and I won't go back.  If this does not work for you, let us know here and we'll try to go a different route.

In more direct response to your inquiry, I think that having your email read and then execute commands would be considered a **major** security no-no.  If you can execute commands on your server in this method, why can't I?

---

### Post by drumfire420 on 2009-05-13
as far as security:
A:I was hoping there would be a way to code it so that it would only work with my particular cell number.
B:I was also hoping there would be a way to only allow certian scripts *like triggering commands based off of keywords*
C:Anything worth keeping is on other computers, so feel free to hack this one, this is a play thing ;)

for functionality:
This would allow me to evolve a service closer to Google SMS, or a chat bot.  allowing me to write a script to check status of anything atainable by CLI on my computer ... This would not be avaialable using the dyndns/ssh method, as I could not do that from my cellphone.

---

### Post by gradysghost on 2009-05-22
Well, to be honest, I don't really know how I would go about setting something like that up.  Still, if your phone supports it or has an available app (G1 with Android, iPhone, etc.), you should look into SSH.  Control simply does not get more complete than that.

---


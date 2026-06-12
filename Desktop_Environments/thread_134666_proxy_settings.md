---
title: "proxy settings"
date: 2006-02-22
forum: Desktop Environments
---

### Post by Strannik on 2006-02-22
I added the "Weather Report" item to the top panel in Gnome. But the thing does not want to go through the network proxy to the internet. i put the proxy settings in applications>system tools>configuration editor; in /etc/bash.bashrc: export http_proxy='http://192.168.1.1:3128' and it stills doesn't update... all it says is : updating. can somebody point me to some system wide proxy setting config file or just for this thing??? it really bothers me that i can't find out the temperature outside.
any help is most appreciated

---

### Post by dcstar on 2006-02-23
[QUOTE=Strannik]I added the "Weather Report" item to the top panel in Gnome. But the thing does not want to go through the network proxy to the internet. i put the proxy settings in applications>system tools>configuration editor; in /etc/bash.bashrc: export http_proxy='http://192.168.1.1:3128' and it stills doesn't update... all it says is : updating. can somebody point me to some system wide proxy setting config file or just for this thing??? it really bothers me that i can't find out the temperature outside.
any help is most appreciated[/QUOTE]
So the System-Preferences-Network Proxy tool doesn't work?

---

### Post by Strannik on 2006-02-23
yes...it doesn't work. I tried entering "192.168.1.1" and "http://192.168.1.1" just in case...and no luck with anything.... would really like to know in what config files are the proxy settings listed...

---

### Post by Strannik on 2006-02-23
does anybody know where i sould put my proxy settings for the whole system?

---

### Post by lamego on 2006-02-23
There is no such thing as setting up the proxy for the whole system.
The most common way to setup a proxy for terminal application is to define the http_proxy environment as you already did.
The place for gnome and gnome apps is System->Preferences->Network Proxy ,
If it is a gnome application and it doesn't work then it does not support proxy configuration.
So far I have used some of of the gnome applets with proxy without any problems...

Please note that some applications have their own file/place for the proxy configuration (e.g. firefox).

---

### Post by Strannik on 2006-02-23
ok, thanks. This same thing works on my friends computer also through the same proxy, so this app does work through a proxy...just don't know how to make it work correctly =)

---

### Post by lamego on 2006-02-23
Are you able to use the same proxy with firefox ?
Maybe it requires authentication ?

---

### Post by barmaley on 2006-04-04
Hello, people

I have the same problem with the WeatherReport: it works at home (without proxy) and doesn't do at work with the proxy. I wonder if you have solved the problem and how?
Not a serious problem but just bothers me, since I don't use firefox.

---


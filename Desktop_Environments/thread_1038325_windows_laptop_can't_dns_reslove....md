---
title: "windows laptop can't dns reslove..."
date: 2009-01-12
forum: Desktop Environments
---

### Post by hockey97 on 2009-01-12
Hi, My friends laptop that has windows os can't dns reslove.

I notice if you use IE7 or firefox3 and type in [www.google.com](www.google.com) it won't find the site however when you  type in googles ip address it finds the website.

the dns configs are right. It just the computer can'f resolve to the hostnames.

how can I fix this??? it seems soemthing is going wrong with the laptop like if some files are missing that prevents the laptop to understand the dns server.

I am using the same dns server ip and it works for me yet it dosen't work on the laptop?

what can I do to fix this?

my anti-virus programs wont update on the laptop cause it uses hostnames to grab the files from web servers to update the app.

any ideas??

---

### Post by stefangr1 on 2009-01-12
Your problem could have multiple causes as to why the windows-xp pc can't find the dns server. As a workaround you could always see what the address of your internet provider's dns server is, and type it in manually in the browser.

For troubleshooting you should provide some more information about your specific setup, and: when you open the cmd in windows xp, and type in "ipconfig -all", does windows return the right dns server?

---

### Post by hockey97 on 2009-01-12
ok, I have tried ipconfig /all which shows all the right information.

I did a nslookup I get a dns cannont be found error.

I do get a ip address from my router. 

In the web browser I can type the ip address to get the site but can't get the site by the host name meaning [www.google.com](www.google.com)

So I know it's not a connection problem. I also turned off mac list banning from my router. I deleted macaffee thinking it could be the cause of the problem.

i done also a sfc /scannow which didn't really nothing a window poped up and showed a loading bar.

after the whole day debugging.. I can say it seems like the laptop can't communicate to the dns server.

Some people told me maybe it's my dsn config is wrong so they give me 2 ip addresses of a free well known dns server and I set it to that which still didn't work.

I currently don't know why the laptop can't reslove to hostnames.

I done the basic stuff.. like ipconfig /all  and nslookup.

what can I do to try and fix it. 


All I can say that the laptop is getting a internet connection and has the right dns servers.

but checking with nslookup it seems the laptop is not connecting to the dns server.

I think it might be missing any files that would deal with connecting and communicated with the dns servers.

just my guess.

anything else please tell me what else I should try to check.

---

### Post by stefangr1 on 2009-01-12
Puzzling... Can you maybe post the result of ipconfig -all ?

---

### Post by hockey97 on 2009-01-12
well I don't think I can. 

it did the ipconfig -all again and I notice dhcp is not enabled.

---

### Post by stefangr1 on 2009-01-12
> **hockey97 said:**
> well I don't think I can. 

it did the ipconfig -all again and I notice dhcp is not enabled.

Sorry, I don't know. The domain name seems not to be connected to a specific ip-addres.

If you have a look at Configuration screen -->  Network + Internet connections --> Network connections --> right click on LAN and go to the characteristics --> Internet-protocol TCP/IP --> click on characteristics

is automatic ip-address and DNS server address enabled?

---

### Post by hockey97 on 2009-01-12
yes they are automaticly enabled. 

I been playing around making a manuel config with dns servers that are free.

I notice alot of people are just reinstalling windows and saying that did the trick. Some people say to remove macaffee. Others said to remove avg.

the  config is proper. I know for sure. It's the same config my computers are using and I have no problem.

it seems like the name server lookup is currpted. I mean like I think it's the laptop itself. cause my other laptops have no trouble with the same config.  I know the internet connection is working and that laptop could connected to computers only by ip address.

this is how I transfered anti-virus apps from my desktop computer using a web server to the laptop and installed the apps on there only the ones that didn't requrie a internet connection.

spybot requires a internet connection so it kept failing.

I am really stumped.

I know it's a dns issue. The problem lays in the laptop. The laptop can't plain out talk with the dns servers. I tried many. 

so the laptop is messed up.

Should I just tell my friend to take it to a repair shop???

I assume they will say to reinstall windows xp.

cause I can't find a solution online using google.

---


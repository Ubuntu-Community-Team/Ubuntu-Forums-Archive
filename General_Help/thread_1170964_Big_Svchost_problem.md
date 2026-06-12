---
title: "Big Svchost problem"
date: 2009-05-26
forum: General Help
---

### Post by Zemptang on 2009-05-26
I need help badly... i know multiple svchosts are common, but i have 17 running.... one is even over 60k

is this a problem or no?

[IMG]http://img.photobucket.com/albums/v131/sexymanpoint5/Untitled-1.jpg[/IMG]

---

### Post by s3MA00RRNY on 2009-05-26
Welcome to the _***Ubuntu***_ forums ZempTang! Svchost is the Windows Service Host, which manages services run as DLLs. To turn off some of the services and get back some of that memory go to Start > Run... and type in services.msc and press enter. Change any services you don't need to run to disabled. Be very careful though. Don't disable something if you don't know what it does.

---

### Post by doas777 on 2009-05-26
it's fine. vista uses a service host process for each service interface. xp and prev shared the host process so there didn't seem to be as many of them as there are now. they're usually pretty light, but if you have one you don't want, try disabling the coresponding service, in services.msc

---

### Post by Zemptang on 2009-05-26
ok so i know this sounds dumb but will that tell me what program is causing it?

---

### Post by doas777 on 2009-05-26
> **Zemptang said:**
> ok so i know this sounds dumb but will that tell me what program is causing it?

well the trite answer is 'Windows'.

ok, go to the administrative tools folder and launch "Services".

all of the services that make windows be are listed here (well most of them).
most of the items in this list, that are set with a startup type of 'Automatic' are run within a svchosts.exe process.

if you download process explorer, and enable the "Command Line" collumn, you will be able to see the exact executable and switches used for each svchosts process/.

alternatively you can go to a command prompt and put in:
```
tasklist /SVC > c:\services.txt
``` 
once the command is done, go to see and open services.txt to see which service runs in each svchosts instance.

the "sc" command also alows you to monitor and control services. may be of use.

---

### Post by rehilliard on 2009-05-26
Download and install Russinovich's Process Explorer. It'll show you what's associated with the svchost processii. 

[http://technet.microsoft.com/en-us/sysinternals/bb896653.aspx](http://technet.microsoft.com/en-us/sysinternals/bb896653.aspx)

"Scroll through the list of processes until you see the SVCHOST.EXE    process(es). To find out which services are running within a particular SVCHOST.EXE    process we need to examine the properties for the process. To do this double-click    SVCHOST.EXE entry in Process Explorer and you will see the properties screen    for the process like in the image below." (see image)

---


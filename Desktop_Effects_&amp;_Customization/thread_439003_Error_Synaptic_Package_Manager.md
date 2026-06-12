---
title: "Error Synaptic Package Manager"
date: 2007-05-10
forum: Desktop Effects &amp; Customization
---

### Post by flayofish on 2007-05-10
Hello,
This is my first time experience with Linux, so be gentle  :( 
I'm following a "How To" install and configure Ubuntu from and article off maximumpc.com
Part of the configuration talks about installing Beryl.
I followed the instructions:
adding: deb [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty main    to repository list.
opening terminal and typing: wget [http://ubuntu.beryl-project.org/@lupine.me.uk.gpg](http://ubuntu.beryl-project.org/@lupine.me.uk.gpg) -O- | sudo apt-key add -
It appears to complete, then I finish adding repository.
When I refresh the list, so Beryl appears, I get the following error:
W: GPG error: [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3FF0DB166A7476EA

Beryl does not appear in the list, either.

Any help appreciated.

-thanks

---

### Post by Kobalt on 2007-05-10
Hello,

What happens when you copy/paste this into the Terminal : 
```
wget http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg -O- | sudo apt-key add -
```

---

### Post by bloodniece on 2007-05-10
The URL for that key is giving me a 404 when I try to access it.

```
$ wget http://ubuntu.beryl-project.org/@lupine.me.uk.gpg -O- | sudo apt-key add -
Password:--08:58:31--  http://ubuntu.beryl-project.org/@lupine.me.uk.gpg
           => `-'
Resolving ubuntu.beryl-project.org... 195.114.19.35, 208.113.193.9, 80.77.247.17, ...
Connecting to ubuntu.beryl-project.org|195.114.19.35|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
08:58:33 ERROR 404: Not Found.
```Looks like the link is bad or down.

---

### Post by Kobalt on 2007-05-10
I just tried it manually and I can download the GPG key... 
You can try this as well : download it and manually add it to System > Admin. > Update sources : Identification (or something like that, sorry my Ubuntu is in French not in English).

---

### Post by flayofish on 2007-05-10
> **Kobalt said:**
> Hello,

What happens when you copy/paste this into the Terminal : 
```
wget http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg -O- | sudo apt-key add -
```

Here is the response in terminal:

--09:04:57--  [http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg](http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg)
           => `-'
Resolving ubuntu.beryl-project.org... Password:88.191.250.18, 80.77.247.17, 82.140.42.54, ...
Connecting to ubuntu.beryl-project.org|88.191.250.18|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2,415 (2.4K) [application/x-troff-me]

100%[====================================>] 2,415         --.--K/s             

09:04:57 (88.65 MB/s) - `-' saved [2415/2415]

I get the same error when i try to refresh the list after running command in terminal.

---

### Post by flayofish on 2007-05-10
> **Kobalt said:**
> I just tried it manually and I can download the GPG key... 
You can try this as well : download it and manually add it to System > Admin. > Update sources : Identification (or something like that, sorry my Ubuntu is in French not in English).

Pardon my ignorance, but how do I go about downloading it manually?  I tried going to System > Admin > Update Manager as well... same result.

---

### Post by Kobalt on 2007-05-10
The command seem to have worked in Terminal. Have you run this command afterwards : ```
sudo apt-get update
```

---

### Post by flayofish on 2007-05-10
> **Kobalt said:**
> The command seem to have worked in Terminal. Have you run this command afterwards : ```
sudo apt-get update
```

Thank you.  That command seemed to stop the error from occurring.
Now downloading a ton of Beryl stuff... smells like a reimage, but that's half the fun  :guitar:

---

### Post by Kobalt on 2007-05-10
Remember you need to run that command anytime you add a repository and/or a GPG key.

---

### Post by SilverDragon on 2007-05-13
I tried sudo apt-get update and then I went to reload and it didn't work :(
My error message is:

W: GPG error: [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3FF0DB166A7476EA

I think the error messages are the same, so I'm not sure why this isn't working :(
I'm following the same instructions from the same article.

I'm going to include the terminal message too:

huy@huy-desktop:~$  wget [http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg](http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg) -O- | sudo apt-key add –
Password:--15:36:24--  [http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg](http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg)
           => `-'
Resolving ubuntu.beryl-project.org... 80.77.247.17, 82.140.42.54, 88.191.250.18, ...
Connecting to ubuntu.beryl-project.org|80.77.247.17|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2,415 (2.4K) [application/x-troff-me]

100%[====================================>] 2,415         --.--K/s             

15:36:24 (71.47 MB/s) - `-' saved [2415/2415]

Is there anything else I can try?

---


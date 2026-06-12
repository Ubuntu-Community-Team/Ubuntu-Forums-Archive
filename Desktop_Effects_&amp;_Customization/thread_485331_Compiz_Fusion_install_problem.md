---
title: "Compiz Fusion install problem"
date: 2007-06-26
forum: Desktop Effects &amp; Customization
---

### Post by 213374U on 2007-06-26
This is also up in the sticky thread. Just want to get an answer as fast as possible. Thanks.

Searched the entire thread and couldn't find an answer to my question. To "Add Keys" simply copy and paste into terminal, correct? If so, after I do that, it adds one key. Then when I run 

```
sudo apt-get update
```

It gives me this

```

Get:1 http://us.archive.ubuntu.com feisty Release.gpg [191B]
Ign http://us.archive.ubuntu.com feisty/main Translation-en_US                 
Ign http://us.archive.ubuntu.com feisty/restricted Translation-en_US           
Get:2 http://security.ubuntu.com feisty-security Release.gpg [191B]            
Ign http://security.ubuntu.com feisty-security/main Translation-en_US          
Ign http://security.ubuntu.com feisty-security/restricted Translation-en_US    
Ign http://us.archive.ubuntu.com feisty/universe Translation-en_US             
Ign http://us.archive.ubuntu.com feisty/multiverse Translation-en_US 
Get:3 http://us.archive.ubuntu.com feisty-updates Release.gpg [191B]
Ign http://us.archive.ubuntu.com feisty-updates/main Translation-en_US       
Ign http://us.archive.ubuntu.com feisty-updates/restricted Translation-en_US
Hit http://us.archive.ubuntu.com feisty Release                      
Ign http://security.ubuntu.com feisty-security/universe Translation-en_US      
Ign http://security.ubuntu.com feisty-security/multiverse Translation-en_US    
Get:4 http://download.tuxfamily.org feisty Release.gpg [189B]                  
Ign http://download.tuxfamily.org feisty/eyecandy Translation-en_US            
Hit http://security.ubuntu.com feisty-security Release                         
Hit http://us.archive.ubuntu.com feisty-updates Release             
Get:5 http://download.tuxfamily.org feisty Release [10.5kB]                    
Hit http://security.ubuntu.com feisty-security/main Packages               
Hit http://us.archive.ubuntu.com feisty/main Packages                      
Hit http://us.archive.ubuntu.com feisty/restricted Packages
Hit http://us.archive.ubuntu.com feisty/main Sources                       
Hit http://us.archive.ubuntu.com feisty/restricted Sources                 
Hit http://security.ubuntu.com feisty-security/restricted Packages
Hit http://security.ubuntu.com feisty-security/main Sources
Hit http://security.ubuntu.com feisty-security/restricted Sources
Ign http://download.tuxfamily.org feisty Release                      
Hit http://us.archive.ubuntu.com feisty/universe Packages             
Hit http://us.archive.ubuntu.com feisty/universe Sources
Hit http://us.archive.ubuntu.com feisty/multiverse Packages          
Hit http://us.archive.ubuntu.com feisty/multiverse Sources           
Hit http://us.archive.ubuntu.com feisty-updates/main Packages
Hit http://security.ubuntu.com feisty-security/universe Packages
Hit http://security.ubuntu.com feisty-security/universe Sources
Hit http://security.ubuntu.com feisty-security/multiverse Packages   
Hit http://security.ubuntu.com feisty-security/multiverse Sources    
Get:6 http://download.tuxfamily.org feisty/eyecandy Packages [14.3kB]
Hit http://us.archive.ubuntu.com feisty-updates/restricted Packages
Hit http://us.archive.ubuntu.com feisty-updates/main Sources
Hit http://us.archive.ubuntu.com feisty-updates/restricted Sources
Get:7 http://download.tuxfamily.org feisty/eyecandy Sources [37B]
Fetched 25.1kB in 1s (20.2kB/s)
Reading package lists... Done
[b]W: GPG error: http://download.tuxfamily.org feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2D6CFB44DD800CD9
W: You may want to run apt-get update to correct these problems[/b]

```

Tried getting this running before and couldn't. I'm now on a fresh Ubuntu install (Feisty) and I still got this. Haven't proceeded any further because I think this is where the hang up is.

---

### Post by mid_night gypsy on 2007-06-26
213374U

  I think this is the key you need, if for eyecandy
 ```
    wget http://download.tuxfamily.org/3v1deb/DD800CD9.gpg -O- | sudo apt-key add -


```
       hope this helps,gypsy

---

### Post by Vorian on 2007-06-26
> **mid_night gypsy said:**
> 213374U

  I think this is the key you need, if for eyecandy
 ```
    wget http://download.tuxfamily.org/3v1deb/DD800CD9.gpg -O- | sudo apt-key add -


```       hope this helps,gypsy

Without this key^, you will continue to get this:
> W: GPG error: [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2D6CFB44DD800CD9
W: You may want to run apt-get update to correct these problems

---


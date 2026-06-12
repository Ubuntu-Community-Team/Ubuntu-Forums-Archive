---
title: "wget does not work"
date: 2009-01-14
forum: General Help
---

### Post by b-boy on 2009-01-14
Hi guys 

When i try to wget something  from the bash command line I get and error. 

**This is my command **
```
wget http://URL
```

**and this is the error**
```
Error parsing proxy URL http://username:password@myproxy.co.za:8080/: Bad port number.
```

**More info**
I do have a proxy at work and Wget worked before through my proxy. My friends at work dont have a problem.

Also if I paste the command ```
wget http://URL
``` in a firefox browser it works 

What could be wrong please help

---

### Post by blazemore on 2009-01-14
if you do
```
wget http://[b]remotelocation:80
```
Does it work?

---

### Post by hangfire on 2009-01-14
> **b-boy said:**
> When i try to wget something  from the bash command line I get and error. 

Your FF understands your proxy, while wget does not... yet.

Try something like:

```
export http_proxy="http://proxy.company.com:8080/"
wget --proxy-user=*user* --proxy-password=*password* http://URL
```

Also, Read this:

[http://www.gnu.org/software/wget/manual/html_node/Proxies.html#Proxies]("http://www.gnu.org/software/wget/manual/html_node/Proxies.html#Proxies")

-HF

---

### Post by b-boy on 2009-01-15
> **blazemore said:**
> if you do
```
wget http://[b]remotelocation:80
```
Does it work?

still the same error

---

### Post by b-boy on 2009-01-15
> **hangfire said:**
> Your FF understands your proxy, while wget does not... yet.

Try something like:

```
export http_proxy="http://proxy.company.com:8080/"
wget --proxy-user=*user* --proxy-password=*password* http://URL
```

Also, Read this:

[http://www.gnu.org/software/wget/manual/html_node/Proxies.html#Proxies]("http://www.gnu.org/software/wget/manual/html_node/Proxies.html#Proxies")

-HF

when i try the above i get 2009-01-15 12:28:07 ERROR 403: Forbidden

this occurs aswell if a friend put his details

---

### Post by hangfire on 2009-01-15
> **b-boy said:**
> when i try the above i get 2009-01-15 12:28:07 ERROR 403: Forbidden

Please post the actual wget command line you were trying, *minus password of course*. (The text I posted was generic). We'll find out what makes Firefox work, and then use that for wget.

So, please post a screenshot of the Firefox Edit->Preferences->Advanced->Network Tab->Connection->Connection Settings menu.

Also please post the Acquire line from file **/etc/apt/apt.conf** .

And, Gnome (I think):
System -> Preferences -> Network Proxy 

-Or- KDE:
K->System Settings->Network Settings->Proxy



Thanks.
-HF

---

### Post by b-boy on 2009-01-15
> Please post the actual wget command line you were trying, *minus password of course*. (The text I posted was generic). We'll find out what makes Firefox work, and then use that for wget.
wget --proxy-user=username --proxy-password=password http:URL

> 
So, please post a screenshot of the Firefox Edit->Preferences->Advanced->Network Tab->Connection->Connection Settings menu.
I have this set to use system proxy
> 
Also please post the Acquire line from file **/etc/apt/apt.conf** .

I dont have that config file

> And, Gnome (I think):
System -> Preferences -> Network Proxy 


this is set maually in this format [http://proxy.co.za:8080](http://proxy.co.za:8080)

and i click on authenticate where i enter username and password

---


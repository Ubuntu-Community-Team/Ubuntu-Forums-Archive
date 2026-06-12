---
title: "Automatic Web Page Refresher"
date: 2009-01-05
forum: General Help
---

### Post by Toaster34 on 2009-01-05
Hello All, 

I am looking for an automatic web page refresher that works in Ubuntu. I have seen a bunch out there that are only made for windows. 

Reason: My friends band needs to get a lot of hits on their myspace page so that club owners will consider them. I thought this would be more affective than having 1000 people hit refresh 1000 times. 

Any help would be appreciated. Thanks!

Toast

---

### Post by Ahadiel on 2009-01-05
> **Toaster34 said:**
> Hello All, 

I am looking for an automatic web page refresher that works in Ubuntu. I have seen a bunch out there that are only made for windows. 

Reason: My friends band needs to get a lot of hits on their myspace page so that club owners will consider them. I thought this would be more affective than having 1000 people hit refresh 1000 times. 

Any help would be appreciated. Thanks!

Toast
[This]("https://addons.mozilla.org/en-US/firefox/addon/115") perhaps?

---

### Post by pytheas22 on 2009-01-05
There are Firefox extensions, e.g. [this one]("https://addons.mozilla.org/en-US/firefox/addon/115"), that can do stuff like this.  You could also write a script using wget, for example.

But any decent hit counter is going to know what you're doing, which is basically click fraud, although in the case of Myspace I don't think it matters.

---

### Post by eBoxNet on 2009-01-05
you can create a new html file and add the code bellow to refresh the given website every 15 seconds..ofcourse this will only work if your friends profile has a VERY VERY simple hit counter.it ONLY works with poor free hitcounters.

```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" lang="pl" xml:lang="pl">
<META HTTP-EQUIV="Refresh"
CONTENT="15;>
<head>
<title>Javascript IFrame Reload</title>
<meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
</head>
<body>
<iframe id="reloader" width="500" height="400" src="YOUR FRIEND'S WEBPAGE"/>
</body>
</html>
```

---

### Post by smo0th on 2009-02-27
thanx for the script ebeBoxNet, it works sweet!! :) just to mention there's a typo with CONTENT="15;> which should be CONTENT="15;"> but anyway, I mention this only for people who really don't have a clue on html.

cheers

---


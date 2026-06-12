---
title: "How to return only the matched substring in BASH (not the entire line)?"
date: 2009-06-07
forum: General Help
---

### Post by biodiesel-bri on 2009-06-07
This has to be easy but I can't figure it out.  I'm working on a shell script to pull image URLs from html files, and I have a regex that properly matches the entire line when scanning html files, but all I want is the substring.  

Here's the (pretty sad) regex that returns the line:
```
grep 'http[A-Z0-9a-z\:\/.\/\?=%&;]*AnimalPictures[A-Za-z0-9\?\:=%&;]*'
```

Here's the correct matching line from the html file:
```
<a href="http://foo.bar.com/FooBar/baz/AnimalPictures?oid=oid%9Z4066887&amp;image=oid%9Z4066886"><img src="1e462z08b5d733f2a8a634c22f66cd48--1--POLARBEARjpg--medium.jpg" width="200" height="254" alt="polar bear" border="0"></a><br>
```

I don't want the whole line, I just want this part: 
```
http://foo.bar.com/FooBar/baz/AnimalPictures?oid=oid%9Z4066887&amp;image=oid%9Z4066886
```

I've tried sed and BASH, read a bunch of tutorials, but I still can't figure it out.  Any ideas?

---

### Post by unutbu on 2009-06-07
```
grep -o 'http[A-Z0-9a-z\:\/.\/\?=%&;]*AnimalPictures[A-Za-z0-9\?\:=%&;]*' FILENAME
```

-o flag FTW!

---

### Post by biodiesel-bri on 2009-06-07
That did it, thank you!!

---


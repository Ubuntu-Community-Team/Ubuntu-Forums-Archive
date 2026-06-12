---
title: "program to dowload lots of links"
date: 2009-05-27
forum: General Help
---

### Post by Twallaroo on 2009-05-27
Hi all,

Does any of you know a good program to download a lot of links in parallel and/or queue them?
I'm looking for something to download lot's of items from rapidshare.
In windows I used flashget and raget.

Thanks

---

### Post by ActiveFrost on 2009-05-27
download.sh : 
```
wget http://www.domain.com/file1.rar
wget http://www.domain.com/file2.rar
wget http://www.domain.com/file3.rar

```

chmod download.sh to 755 ( or 777 ) and run it .. ;)

---

### Post by urgnom on 2009-05-27
Using wget is a good idea. If you want to do more (and who doesn't) you can use a script to parse the entire web site, extract all links, filter them and download thost that go through your filter. Better than manually adding links if we are talking like thousands... :-) Good luck! (I suggest Python - very good HTML parsing there!)

---

### Post by Twallaroo on 2009-05-27
Thanks for the response.
I was actually looking for a GUI program.

Using wget to get rapidshare files seems to be a bit sticky.
I first need to create a cookie with my credentials.
If any one else is looking for this, I did the following:


[LIST]
[*]cd /media/data
[*]mkdir download
[*]cd download
[*]mkdir .cookie
[*]wget --save-cookies .cookies/rapidshare --post-data "login=<my_login>&password=<my_pwd>" -O - [https://ssl.rapidshare.com/cgi-bin/premiumzone.cgi](https://ssl.rapidshare.com/cgi-bin/premiumzone.cgi) > /dev/null
[*]I copy/pasted all the links in a file called 'links'
[*]for link in `cat links`; do wget -c --load-cookies .cookies/rapidshare $link; done
[/LIST]
Thanks for the help anyway.
If someone still has a GUI, please let me know

---

### Post by Ms_Angel_D on 2009-05-27
You could try [downthemall]("https://addons.mozilla.org/en-US/firefox/addon/201")

if the links are clickable links there is a button (which you'll have to drag to your firefox toolbar) that let's you download all the current links on a page and you can filter by file type.

---

### Post by izak on 2009-06-01
[Flashget in wine]("http://ubuntuforums.org/showthread.php?p=7380441#post7380441") works well out of the box.

---

### Post by binbash on 2009-06-01
Jdownloader is the best application to download from file hosting sites like rapidshare :

[http://www.ubuntu-inside.me/2009/02/jdownloader-ultimate-freepremium.html](http://www.ubuntu-inside.me/2009/02/jdownloader-ultimate-freepremium.html)

---

### Post by Twallaroo on 2009-06-01
Thanks BinBash,

That was what I was looking for.

---


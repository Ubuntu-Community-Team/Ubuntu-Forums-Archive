---
title: "regex Help"
date: 2009-05-31
forum: General Help
---

### Post by yma981 on 2009-05-31
Hello 

I use imglikeopera Firefox extension to block images and I usually use filters.

I am trying to allow all images that follow this pattern to load 

[http://wwwq3.megaupload.com/gencap.php?ae24e261b149110f.gif](http://wwwq3.megaupload.com/gencap.php?ae24e261b149110f.gif)
[http://wwwq2.megaupload.com/gencap.php?23b6f391254caa6e.gif](http://wwwq2.megaupload.com/gencap.php?23b6f391254caa6e.gif)
                  
So I am using this regex to match with these pictures

/http://wwwq[0-100]\.megaupload\.com/gencap\.php*/

And different flavors of this regex

But it is not working 

Any idea please ???

---

### Post by unutbu on 2009-05-31
This should work:
```
/http:\/\/wwwq[0-9]*\.megaupload\.com\/gencap\.php.*/
```

---

### Post by mobilediesel on 2009-05-31
> **yma981 said:**
> Hello 

I use imglikeopera Firefox extension to block images and I usually use filters.

I am trying to allow all images that follow this pattern to load 

[http://wwwq3.megaupload.com/gencap.php?ae24e261b149110f.gif](http://wwwq3.megaupload.com/gencap.php?ae24e261b149110f.gif)
[http://wwwq2.megaupload.com/gencap.php?23b6f391254caa6e.gif](http://wwwq2.megaupload.com/gencap.php?23b6f391254caa6e.gif)
                  
So I am using this regex to match with these pictures

/http://wwwq[0-100]\.megaupload\.com/gencap\.php*/

And different flavors of this regex

But it is not working 

Any idea please ???

```
/http:\/\/wwwq[COLOR="Red"]**[0-9]\{1,3\}**[/COLOR]\.megaupload\.com\/gencap\.php*/
```

inside the [ ] only matches one character so the [0-9] will match any digit 0-9, the \{1,3\} tells it to match that digit at least once, up to 3 times. the slashes need backslashes to be escaped, too.

---

### Post by yma981 on 2009-05-31
> **unutbu said:**
> This should work:
```
/http:\/\/wwwq[0-9]*\.megaupload\.com\/gencap\.php.*/
```

@unutbu:    Thkx alot unutbu, I tried it it worked great :) I really appreciate it
	

@mobilediesel

Code:
 	/http:\/\/wwwq[COLOR=Red]**[0-9]\{1,3\}**[/COLOR]\.megaupload\.com\/gencap\.php*/ 
This regex didn't work, thank you for your precious information :)

---

### Post by mobilediesel on 2009-05-31
> **yma981 said:**
> @unutbu:    Thkx alot unutbu, I tried it it worked great :) I really appreciate it
	

@mobilediesel

Code:
 	/http:\/\/wwwq[COLOR=Red]**[0-9]\{1,3\}**[/COLOR]\.megaupload\.com\/gencap\.php*/ 
This regex didn't work, thank you for your precious information :)

I totally didn't notice the missing dot near the end that Unutbu put there. I think that's why that one worked and mine didn't. Also Unutbu put a * after the [0-9] which would match any number of digits which is probably better for your purpose anyway. Computers will always do what you tell them to, but it wont necessarily be what you want them to do. :)

I've actually gotten into learning the regexes kind of recently so I'm not too surprised I missed something. Oh well.

---

### Post by VMC on 2009-05-31
By the way, if you want to test your regex script go [HERE]("http://www.regextester.com/").

---


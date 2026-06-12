---
title: "shell script help"
date: 2008-12-17
forum: General Help
---

### Post by dbrooke on 2008-12-17
Hello!

My command line ability is at the "occasional hobby" state.. and I could use some help.

I'm looking for a couple command lines to add to a shell script.

I want edit a file specifically after a matched expression.

For example:

If i have a text file called flinstones.txt with this contents:

--flinstones.txt--
Fred
Wilma
Barney
--

But I wanted to add "dino" just after Wilma:

to look like:
Fred
Wilma
Dino
Barney

How would I do that on the fly within a shell script?
I know I can do that manually using vi or something.. but
I want to match "Wilma".. then add a return and "dino", then save.. all on the fly.

Thanks for the help!

Donovan

---

### Post by hal8000 on 2008-12-17
> **dbrooke said:**
> Hello!

My command line ability is at the "occasional hobby" state.. and I could use some help.

I'm looking for a couple command lines to add to a shell script.

I want edit a file specifically after a matched expression.

For example:

If i have a text file called flinstones.txt with this contents:

--flinstones.txt--
Fred
Wilma
Barney
--

But I wanted to add "dino" just after Wilma:

to look like:
Fred
Wilma
Dino
Barney

How would I do that on the fly within a shell script?
I know I can do that manually using vi or something.. but
I want to match "Wilma".. then add a return and "dino", then save.. all on the fly.

Thanks for the help!

Donovan


Well I'll start this for you, its easy to append to a file using the echo command and >> redirect command
E.G

echo "dino"" >> flinstones.txt

will automatically append the text dino to your file and save it,
its not in the order you'd like but its a start.

---

### Post by eraker on 2008-12-17
Sed is good for stuff like this. It will find and replace throughout a file using the syntax:
```
sed -e 's/thing to find/thing to replace with/g' filename
```

So what you have to do is tell sed to look for a line that ends "wilma" and then replace that line with itself and a new line with the new text.

Here's a very limited version of that which isn't good for much else:

```
sed -e 's/\(a$\)/\1 \nDino/g' flintstones.txt
```

This tells sed to find the line that ends with an "a", then to substitute that information for itself (the first thing captured) "\1", then throw in a newline "\n" immediately after, then throw in the word "Dino". Also, the \( and \) stuff means "capture this information because I want to keep it or use it later."

By the way, if you're going to be doing this a lot, the best thing to learn is regular expressions (regex) because it makes finding complex stuff with sed and other tools a lot easier.

---

### Post by dbrooke on 2008-12-17
> **hal8000 said:**
> 

echo "dino"" >> flinstones.txt


Well, I *do* need this as well. One question.. how would you
add a cr (return) after dino?

Thanks,
Donovan

---

### Post by hal8000 on 2008-12-17
> **dbrooke said:**
> Well, I *do* need this as well. One question.. how would you
add a cr (return) after dino?

Thanks,
Donovan

There's a lot of escape sequence codes \r should dislay a carriage return, heres another link:

[http://publib.boulder.ibm.com/infocenter/systems/index.jsp?topic=/com.ibm.aix.cmds/doc/aixcmds2/echo.htm](http://publib.boulder.ibm.com/infocenter/systems/index.jsp?topic=/com.ibm.aix.cmds/doc/aixcmds2/echo.htm)

---

### Post by dbrooke on 2008-12-17
> **eraker said:**
> Sed is good for stuff like this. It will find and replace throughout a file using the syntax:
```
sed -e 's/thing to find/thing to replace with/g' filename
```

So what you have to do is tell sed to look for a line that ends "wilma" and then replace that line with itself and a new line with the new text.

Here's a very limited version of that which isn't good for much else:

```
sed -e 's/\(a$\)/\1 \nDino/g' flintstones.txt
```

This tells sed to find the line that ends with an "a", then to substitute that information for itself (the first thing captured) "\1", then throw in a newline "\n" immediately after, then throw in the word "Dino". Also, the \( and \) stuff means "capture this information because I want to keep it or use it later."

By the way, if you're going to be doing this a lot, the best thing to learn is regular expressions (regex) because it makes finding complex stuff with sed and other tools a lot easier.

Thanks!  I will clarify a bit: I'm looking for:

<IfModule mime_module>
within an httpd.conf file..

So maybe something like this?:
```
sed -e 's/\(\<IfModule mime_module\>$\)/\1 \nAddType text\/html \.tpl\n/g' httpd.conf
```


??  Thanks for the help!

Donovan

---

### Post by eraker on 2008-12-17
That should work just fine but you shouldn't have to escape the < & >, so the following won't find your line:
```
sed -e 's/\([COLOR="Red"]\[/COLOR]<IfModule mime_module[COLOR="Red"]\[/COLOR]>$\)/\1 \nAddType text\/html \.tpl\n/g' httpd.conf
```

But this one will:
```
sed -e 's/\(^<IfModule mime_module>$\)/\1 \nAddType text\/html \.tpl\n/g'  httpd.conf
```

(That ^ character means "beginning of line.")

---

### Post by unutbu on 2008-12-17
If you add the -i flag to the sed command, sed will edit httpd.conf in-place and make a backup file called httpd.conf~.
```
sed -e 's/\(^<IfModule mime_module>$\)/\1 \nAddType text\/html \.tpl\n/g' -i~ httpd.conf
```

---

### Post by Slim Odds on 2008-12-17
> **dbrooke said:**
> Well, I *do* need this as well. 

Just exactly how is this script supposed to "know" where you want 'dino' inserted?

---

### Post by dbrooke on 2008-12-17
> **unutbu said:**
> If you add the -i flag to the sed command, sed will edit httpd.conf in-place and make a backup file called httpd.conf~.
```
sed -e 's/\(^<IfModule mime_module>$\)/\1 \nAddType text\/html \.tpl\n/g' -i~ httpd.conf
```


Ahh, that is getting me very close to what I need!

However, couple details.. adding sudo and it is not recognizing the new line:

```
sed -e 's/\(^<IfModule mime_module>$\)/\1 \nAddType text\/html \.tpl\n/g' -i~ httpd.conf
```

results in:
```
<IfModule mime_module> nAddType text/html .tpln
```

Donovan

---

### Post by dbrooke on 2008-12-17
Regarding the sed line:

I've taken this to a shell script.. since I can't seem to get a new line to work. Here is what I have so far (which doesn't work):

```

# /bin/sh
sudo sed -e 's/\(^<IfModule mime_module>$\)/\1 a\
AddType text\/html \.tpl \.dna a\
/g' -i~ httpd.conf

```

(added a .dna suffix as well)

Thanks for any help.

Donovan

---

### Post by unutbu on 2008-12-17
Could you post snippet of httpd.conf and what you want the sed-ified snippet to look like?

---

### Post by ibuclaw on 2008-12-17
If you want to put a line **after** the matched line, use the **/a\** switch in sed, not s/// you wollies :)
```
sed '/\(^<IfModule mime_module>$\)/a\AddType text/html .tpl' -i~ httpd.conf
```

Try it now.

Regards
Iain

---

### Post by dbrooke on 2008-12-17
Solved: 

O.K., the first part of my problem is solved. I can call this shell script, and replace appropriately:

```

sudo sed -e 's/\(^<IfModule mime_module>$\)/\1 \
AddType text\/html \.tpl \.dna\
/g' -i~ httpd.conf

```

Now, I'm trying to do a more easy append of a line (and return) to that httpd.conf file. (appending 1 line at the very bottom)

Ideas on that?

thx,
Donovan

---

### Post by ibuclaw on 2008-12-17
Added '.dna' suffix to the script too.
```
sed -e '/^<IfModule mime_module>$/a\AddType text/html .tpl .dna' -e '$a\ ' -i~ httpd.conf
```

---


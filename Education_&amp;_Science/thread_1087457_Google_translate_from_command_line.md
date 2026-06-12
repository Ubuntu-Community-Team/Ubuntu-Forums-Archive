---
title: "Google translate from command line"
date: 2009-03-05
forum: Education &amp; Science
---

### Post by mag_dex on 2009-03-05
Hi,

I found the Google translate is pretty cool. I would like to use it to translate some text from my computer in batch(in script).

Do you know any way that I could use it easily from shell?

:)

---

### Post by amylase on 2009-03-09
Hi mag_dex

Interesting idea. I never tried it myself but if I were to, my starting point might be using a commandline driven textbased web browser such as Lynx maybe (?) 

[http://lynx.isc.org/](http://lynx.isc.org/)
[http://en.wikipedia.org/wiki/Lynx_(web_browser](http://en.wikipedia.org/wiki/Lynx_(web_browser))

---

### Post by unutbu on 2009-03-10
Save this in ~/bin/translate

[php]#!/usr/bin/env python
from urllib2 import urlopen
from urllib import urlencode
import sys

# The google translate API can be found here: 
# http://code.google.com/apis/ajaxlanguage/documentation/#Examples

lang1=sys.argv[1]
lang2=sys.argv[2]
langpair='%s|%s'%(lang1,lang2)
text=' '.join(sys.argv[3:])
base_url='http://ajax.googleapis.com/ajax/services/language/translate?'
params=urlencode( (('v',1.0),
                   ('q',text),
                   ('langpair',langpair),) )
url=base_url+params
content=urlopen(url).read()
start_idx=content.find('"translatedText":"')+18
translation=content[start_idx:]
end_idx=translation.find('"}, "')
translation=translation[:end_idx]
print translation
[/php]
Make it executable:
```

chmod +x ~/bin/translate
```

Use it like this:
```

translate en es where are you
```
en (English) is the source language
es (Spanish) is the target language
"where are you" is the text to be translated

Output:```

dónde estás
```

---

### Post by mag_dex on 2009-03-10
Thanks! The code is great and works! :)

---

### Post by unutbu on 2009-03-10
I'm glad you like it :D

---

### Post by SoulSmasher on 2009-06-14
excellent! works perfect
i'm not a python guru, but know php. in php, to parse that data, you generally use json_decode. 
i googled a bit, and found this:
[http://docs.python.org/library/json.html](http://docs.python.org/library/json.html)
but wouldn' that be better if this is used?
just my two cents though

Thanks again for the great script! :)

---

### Post by unutbu on 2009-06-15
Thank you very much for the feedback and information, SoulSmasher.
I didn't know about JSON until now. 

Happily, it appears to be quite easy to use json. Below is an updated version of the script.

To use the script with Ubuntu, you'll need to have the python-json package installed. (It requires about 160 KiB to install). 

[PHP]#!/usr/bin/env python
from urllib2 import urlopen
from urllib import urlencode
import sys
try:
    import json
except ImportError:
    print('You need to install the python-json package')
    sys.exit(1)

# The google translate API can be found here: 
# http://code.google.com/apis/ajaxlanguage/documentation/#Examples

lang1=sys.argv[1]
lang2=sys.argv[2]
langpair='%s|%s'%(lang1,lang2)
text=' '.join(sys.argv[3:])
base_url='http://ajax.googleapis.com/ajax/services/language/translate?'
params=urlencode( (('v',1.0),
                   ('q',text),
                   ('langpair',langpair),) )
url=base_url+params
content=urlopen(url).read()
try:
    trans_dict=json.loads(content)
except AttributeError:
    trans_dict=json.read(content)
print(trans_dict['responseData']['translatedText'])[/PHP]

---

### Post by SoulSmasher on 2009-06-15
Hi, thanks for the quick reply unutbu
I tried your new code, as far as i can say it works flawlessly
thank you again for the script, saves me from huge pain :)

---

### Post by lautarop on 2009-06-15
works like a charm
thanks mate

---

### Post by SoulSmasher on 2009-06-17
i found a bug.
when there's ' character inside the text, it won't translate

i.e: try this

translate fr en n'est-ce pas

nothing shows and i've to close it with ctrl+c combination

---

### Post by unutbu on 2009-06-17
Yes, single apostrophes cause a problem with all commands entered into the shell because the shell (bash) interprets the apostrophe as the first of a pair of quotation marks. It's waiting for the closing quotation mark, which never comes.

What I usually do is surround the entire phrase with
double quotation marks:

```
% translate fr en "n'est-ce pas"
is not
```

though this is also possible:
```
% translate fr en n\'est-ce pas
is not
```

---

### Post by SoulSmasher on 2009-06-17
i see, i thought in some way the script could auto escape it, but the terminal prevents that. thanks for the reply :)

---

### Post by tremby on 2009-08-23
I just wrote a slightly more sophisticated script along the same lines. Googled afterwards and found this. Anyway, mine's up at Sourceforge:
[https://sourceforge.net/projects/py-translate/](https://sourceforge.net/projects/py-translate/)

Its usage message:
```
Usage: translate [--help|-h]
                 [--verbose|-v]
                 [-s <source language>] [-d <destination language>]
                 [-f <filename>|<text to translate> ...]

Translate some text from one language to another, giving the result on stdout.

Source language defaults to auto-detection (which can be specified with "-s -") 
and destination language defaults to English. Languages should be entered as 
language codes, for instance en, de, es. Inspect [http://translate.google.com](http://translate.google.com) for 
a full list of supported languages. If auto-detection is used, the language 
detected will be shown on stderr.

If there are no non-option arguments the text to translate is taken from stdin 
by default (which is the same as giving "-f -"). If there are non-option 
arguments these are instead taken as the source text. If you want to use it this 
way, it's best to give the argument "--" to show that no more options will 
appear. Alternatively a file can be used as input by using the -f option.

The --verbose or -v switch enables verbose output.

```

---

### Post by lajevardi on 2009-10-23
SoulSmasher said:> i found a bug.
when there's ' character inside the text, it won't translate
i.e: try this
**translate fr en n'est-ce pas**
nothing shows and i've to close it with ctrl+c combination
That's not a Bug! it's command line & you have to escape certain characters, please try this instead: 
> translate fr en n\'est-ce pas

Great script, thanks unutbu ;)

---

### Post by maxideci on 2010-05-19
> **unutbu said:**
> Save this in ~/bin/translate

[php]#!/usr/bin/env python
from urllib2 import urlopen
from urllib import urlencode
import sys

# The google translate API can be found here: 
# http://code.google.com/apis/ajaxlanguage/documentation/#Examples

lang1=sys.argv[1]
lang2=sys.argv[2]
langpair='%s|%s'%(lang1,lang2)
text=' '.join(sys.argv[3:])
base_url='http://ajax.googleapis.com/ajax/services/language/translate?'
params=urlencode( (('v',1.0),
                   ('q',text),
                   ('langpair',langpair),) )
url=base_url+params
content=urlopen(url).read()
start_idx=content.find('"translatedText":"')+18
translation=content[start_idx:]
end_idx=translation.find('"}, "')
translation=translation[:end_idx]
print translation
[/php]
Make it executable:
```

chmod +x ~/bin/translate
```

Use it like this:
```

translate en es where are you
```
en (English) is the source language
es (Spanish) is the target language
"where are you" is the text to be translated

Output:```

dónde estás
```

unutbu u rawk!!! such cool code...

I tried translating a web page thru command line?? i.e I want to pass an url as an command line argument and get a translated url as output.
for example I would like to convert German web page "http://www.sueddeutsche.de/"  into English, using "http://translate.google.com/?hl=en#" is it possible??

Thanks!!

---

### Post by larryp7639 on 2010-05-19
> **amylase said:**
> Hi mag_dex

Interesting idea. I never tried it myself but if I were to, my starting point might be using a commandline driven textbased web browser such as Lynx maybe (?) 

[http://lynx.isc.org/](http://lynx.isc.org/)
[http://en.wikipedia.org/wiki/Lynx_(web_browser]("http://en.wikipedia.org/wiki/Lynx_%28web_browser"))



Such a very amazing link! 
Thanks you for the post.

---

### Post by maniandram on 2011-08-11
It's not a bug in the program.
Your shell is intrepting the ' to be a quote.
To solve the problem, escape the quote e.g. \':KS

---

### Post by lautarop on 2012-04-27
Hey, is this still working?

---

### Post by ivanzoid on 2012-04-29
> **unutbu said:**
> Save this in ~/bin/translate

[php]#!/usr/bin/env python
from urllib2 import urlopen
from urllib import urlencode
import sys

# The google translate API can be found here: 
# http://code.google.com/apis/ajaxlanguage/documentation/#Examples

lang1=sys.argv[1]
lang2=sys.argv[2]
langpair='%s|%s'%(lang1,lang2)
text=' '.join(sys.argv[3:])
base_url='http://ajax.googleapis.com/ajax/services/language/translate?'
params=urlencode( (('v',1.0),
                   ('q',text),
                   ('langpair',langpair),) )
url=base_url+params
content=urlopen(url).read()
start_idx=content.find('"translatedText":"')+18
translation=content[start_idx:]
end_idx=translation.find('"}, "')
translation=translation[:end_idx]
print translation
[/php]

Hi, I'm getting this error with this script now:

```
null, "responseDetails": "Suspected Terms of Service Abuse. Please see http://code.google.com/apis/errors", "responseStatus": 403
```Probably now we need to pass our google account's cookie somehow?..

---


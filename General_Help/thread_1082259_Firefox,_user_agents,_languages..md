---
title: "Firefox, user agents, languages."
date: 2009-02-27
forum: General Help
---

### Post by detroit/zero on 2009-02-27
I'm using FF 3.0.6 on Hardy.

I'm originally from the US, and speak English, but am currently living in Poland. I have this issue where certain web pages come up automatically in the Polish language, and changing them to English is either not an easy-to-find option, or just not doable.

I of course have everything in my US-bought computer (and my Ubuntu install) set to English. I have the user agent switcher extension installed and set the default language for displaying pages to US English, but this is still happening.

These various websites (blogger.com and wordpress, just to name a couple) must be detecting my IP address and automatically giving me Polish language versions of their pages.

Does anyone know - Is there a way for me to force these pages to come to me in English, or am I just chasing the wind here?

---

### Post by dcstar on 2009-02-28
> **detroit/zero said:**
> I'm using FF 3.0.6 on Hardy.

I'm originally from the US, and speak English, but am currently living in Poland. I have this issue where certain web pages come up automatically in the Polish language, and changing them to English is either not an easy-to-find option, or just not doable.

I of course have everything in my US-bought computer (and my Ubuntu install) set to English. I have the user agent switcher extension installed and set the default language for displaying pages to US English, but this is still happening.

These various websites (blogger.com and wordpress, just to name a couple) must be detecting my IP address and automatically giving me Polish language versions of their pages.

Does anyone know - Is there a way for me to force these pages to come to me in English, or am I just chasing the wind here?

You need to check the header info your browser sends out, sites like [www.grc.com](www.grc.com) can do this for you (in their "Shields Up!!) section.

See what your "Accept-Language" is, mine is "en-au" for English-Australian.

---

### Post by detroit/zero on 2009-02-28
> **dcstar said:**
> You need to check the header info your browser sends out, sites like [www.grc.com]("http://www.grc.com") can do this for you (in their "Shields Up!!) section.

See what your "Accept-Language" is, mine is "en-au" for English-Australian.
I wasn't able to find the header-check at the site you suggested, but I googled and did another one at [http://www.xhaus.com/headers](http://www.xhaus.com/headers)

Here's what they say:

**[EDIT: Screenshot attached. The text output table from that page doesn't sit well in the editor here]**
**[EDIT 2: Had to use Imageshack, instead. For some reason a .png file isn't seen as a valid image format. Forgive the full-sized image, but it's only like 45k.]**

[IMG]http://img24.imageshack.us/img24/719/screenshotcds.png[/IMG]

I see that Polish is an accepted language, but it sort of has to be - I do live in Poland and have to use banking sites, local email for certain things, etc..

One thing I do see in about:config is the string ```
intl.accept_languages;en-us,pl-pl,pl,chrome://global/locale/intl.properties
```I see that the languages are en-us and pl-pl. But I see "pl" appears a second time right after that. Could that be the source of the problem?

Like that string there, I see a number of strings in about:config that point toward *chrome://xxxxxxxx/whatever*, but I can't find where these config files are located. They most assuredly are not in *~/.mozilla/firefox/userprofile/chrome*.

---

### Post by detroit/zero on 2009-03-05
five day bump

---

### Post by detroit/zero on 2009-03-14
> **detroit/zero said:**
> One thing I do see in about:config is the string ```
intl.accept_languages;en-us,pl-pl,pl,chrome://global/locale/intl.properties
```I see that the languages are en-us and pl-pl. But I see "pl" appears a second time right after that. Could that be the source of the problem?
One week bump on the five-day bump.

I did remove the 'pl' options to the accepted languages string in about:config, and that did work on sites like wordpress and blogspot. But YouTube, for example, is using a different method: They detect your IP, figure out what country you're in, and automatically display everything in the language of that country.

Is there any way to keep this from happening, short of using a proxy for everything?

---


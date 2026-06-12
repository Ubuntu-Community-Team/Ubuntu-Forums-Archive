---
title: "reset locale to previous state"
date: 2006-06-20
forum: Desktop Environments
---

### Post by mogliii on 2006-06-20
Hi,

I have installed Xubuntu 6.06 LTS on an veeery old mobile computer (266 Mhz, 60 MB Ram).

I can not say it runs fluent, but it works.

As I want to use this computer also to input japanese, I followed an How-To, that worked for an other computer (Kubuntu with xubuntu-desktop installed).

[https://wiki.ubuntu.com/InputMethods/SCIM/CJK_Chinese_Japanese_Korean_Input_Method_configuration_using_SCIM_in_Ubuntu_6%2e06_Dapper_Drake]("https://wiki.ubuntu.com/InputMethods/SCIM/CJK_Chinese_Japanese_Korean_Input_Method_configuration_using_SCIM_in_Ubuntu_6%2e06_Dapper_Drake")

In this its said, I should open the Language Support, and check Japanese and English (in my case) are available.

Before I did this, I already installed 
```
im-switch language-pack-ja languagae-pack-ja-base mozilla-firefox-locale-ja-jp thunderbird-locale-ja
``` and I could even start a japanese session of Xubuntu.

But back in the english, I started "Language Support", and for english, der was no sign at all, and for japaneses only a dash, instead of a hook. 
He also told me that mozilla_ja or something is missing.

When I checked English, and pressed apply, he told me that he will download and install around 100 MB of data. 

```
aspell aspell-en language-pack-en language-pack-en-base language-support-en language-support-ja mozilla-firefox-locale-en-gb mozilla-firefox-locale-ja myspell-en-gb openoffice.org-**many english and japanese packages** thunderbird-locale-en-gb wamerican wbritisch
```

I canceled the download and installation, cuase this will certainly not increase the speed of the machine. And before I started "Language Support", Everything was working in english.

And if I execute 
```
$ locale -a
C
POSIX
ja_JP.utf8
```

The state now: With POSIX its english, but the fonts dont look nice. Japanese Session still works fine.

so now my question: How to tell my computer to get back to the state before Language Support? How to fix that issue.

Any help apreciated.

---

### Post by mogliii on 2006-06-23
Hi,

After nobody could help me, I decided to install from scratch. And a new Xubuntu English has only POIX as locale. So there was never an utf8 locale for english language.

I will try soon if it is possible to get scim working with POSIX.

---


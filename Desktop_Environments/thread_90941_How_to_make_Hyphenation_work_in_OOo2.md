---
title: "How to make Hyphenation work in OOo2 ?"
date: 2005-11-16
forum: Desktop Environments
---

### Post by davegahan on 2005-11-16
Help. Tried everything, really everything but can't have my documents hyphenated. It gives an error dictionary is not installed (it is) then continues with hyphenation, gives the same error again, and then returns the document unhyphened.

Can anyone please help me out - someone that managed to make it work?

---

### Post by MartinG on 2005-11-16
[QUOTE=davegahan]Help. Tried everything, really everything but can't have my documents hyphenated. It gives an error dictionary is not installed (it is) then continues with hyphenation, gives the same error again, and then returns the document unhyphened.

Can anyone please help me out - someone that managed to make it work?[/QUOTE]

Are you sure the hyphenation dictionary is installed as well as the spelling one? And that it's properly registered in dictionary.lst? I had to do both jobs manually, and my dictionary.lst reads as follows (less the comments):

## !!! BEGIN AUTOMATIC SECTION -- DO NOT CHANGE !!!
## !!! ADD YOUR ADDITIONAL ENTRIES BELOW THIS SECTION !!!
DICT en GB en_GB
DICT en US en_US
THES en US th_en_US_v2
## !!! END AUTOMATIC SECTION -- DO NOT CHANGE !!!
HYPH en GB hyph_en_GB
THES en GB th_en_US_v2

Apart from this I presume all the languages match, and other set up details in OOo's options.

---

### Post by davegahan on 2005-11-16
Thanks for the tip - but where do i find the dictionary.lst file ?

---

### Post by MartinG on 2005-11-16
Sorry -- I should have included this in my first reply. It's in /usr/lib/openoffice2/share/dict/ooo, which is a symlink that takes you to /usr/share/myspell/dicts. It's also in /etc/openoffice -- the system seems to keep them synchronised, I don't know how, and I've always worked with the first one as that's where the dictionaries themselves are. Don't forget you'll need to use sudo to do any editing. 

Hope that helps.

As a more general point you can always find such files by typing locate dictionary.lst (or whatever) in a terminal.

---

### Post by davegahan on 2005-11-16
Thanks a lot. Edited the dictionary.lst file as you suggested. No change though. When I click thesaurus, OOo2 crashes (I did not have the thesaurus function available before the edit).

Sorry, but I installed the US and UK language packs - is there anything I should look at - I even installed through apt-get the Altlinux hyphenator to no avail...

---

### Post by MartinG on 2005-11-16
I didn't use the language pack -- maybe I should have. I grabbed hyph_en_GB.zip from [http://lingucomponent.openoffice.org/hyph_dic.html](http://lingucomponent.openoffice.org/hyph_dic.html), unzipped it and installed it manually into /usr/share/myspell/dicts.  Despite the note on the web page, I can't get the "Install new dictionaries wizard" to work.

What files have you in /usr/share/myspell/dicts? If dictionary.lst points to a non-existent file you WILL have problems!

---

### Post by davegahan on 2005-11-17
Ok 

I have downloaded the hyphenation file and moved it to usr/share/myspell/dicts

Subsequently I have edited my dictionary.lst file accordingly 

## !!! BEGIN AUTOMATIC SECTION -- DO NOT CHANGE !!!
## !!! ADD YOUR ADDITIONAL ENTRIES BELOW THIS SECTION !!!
DICT en GB en_GB
DICT en US en_US
## !!! END AUTOMATIC SECTION -- DO NOT CHANGE !!!
HYPH en GB hyph_en_GB

The contents of the usr/share/myspell/dicts directory are:

/usr/share/myspell/dicts/dictionary.lst
/usr/share/myspell/dicts/en_GB.aff
/usr/share/myspell/dicts/en_GB.dic
/usr/share/myspell/dicts/en-GB.aff
/usr/share/myspell/dicts/en-GB.dic
/usr/share/myspell/dicts/en_US.aff
/usr/share/myspell/dicts/en_US.dic
/usr/share/myspell/dicts/en-US.aff
/usr/share/myspell/dicts/en-US.dic
/usr/share/myspell/dicts/hyph_en_GB.dic

Still it does not work :(
The best for might be to go back to OOo 1.1.4 ?

---

### Post by MartinG on 2005-11-17
Umm ... Yes, I've run out of ideas at this point, I'm afraid. There must be some sort of conflict somewhere. You could try removing OOo2 from your system completely, including your ~/.openoffice.org2 folder (keep a copy of that); don't rely only on synaptic or whatever but do a follow-up search for OOo2 folders across the system.  Then re-install to get a completely virgin set-up and try that.

If it then works you can re-introduce elements from your old ~/.openoffice.org2 folder, keeping copies of whatever you replace in case you stumble across a failure.  Tedious, but it's my last shot.  Best of luck!

---

### Post by davegahan on 2005-11-17
Well I appreciate your help and assistance a lot.

What I did was installing OOo 1.1.5. use the dictionary wizard (which is a macro written by someone) and install the hyphenation and thesaurus dictionaries.
Now it finally works, and I use the 1.1.5. version which I installed from Synaptic alongside OOo 2.0 Awkward but finally I can use hyphenation and thesaurus.

Its a pitty OOo has such awkward routine to install extra dictionaries. I'll subscribe myself to their mailing lists and try to find more out on that side.

Thanks again for your help, if ANYONE out there can provide additional suggestions for Hyphenation and Thesaurus dictionaries on OOo 2, they would be very welcome to do so.

---


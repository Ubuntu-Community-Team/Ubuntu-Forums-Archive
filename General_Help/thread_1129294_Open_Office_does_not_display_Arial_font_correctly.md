---
title: "Open Office does not display Arial font correctly"
date: 2009-04-18
forum: General Help
---

### Post by Corin-EU on 2009-04-18
On Ubuntu 8.10 with OpenOffice 1:2.4.1-11ubuntu2.1 installed, I am having a problem displaying the Arial font.

I have the Arial font installed and if I open a document in AbiWord, the font is correctly displayed as Arial.

However, in OpenOffice if I look at the document all of the text is in upper case, and the font is not Arial, and the drop down font menu list shows the same wrong font under the entry for Arial.

The entries for Arial Black, Arial Narrow, Arial Narrow Special G1, Arial Narrow Special G2, Arial Special G1, and Arial Special G2 all seem to be mapping to the appropriate font.

What do I need to do to fix this problem?

Thank you in advance for your assistance in this matter.

---

### Post by Tahakki on 2009-04-18
Which package did you install? Or is it just a TrueType file?

If you haven't already, try installing the msttcorefonts package. Worked for me.

---

### Post by Corin-EU on 2009-04-18
Thanks for your input.

> **Tahakki said:**
> If you haven't already, try installing the msttcorefonts package. Worked for me.
If I did not have the msttcorefonts installed, I would not be seeing the correct font in Abiword, would I? ;)

A way around the problem has now been found.

It is evident that OpenOffice unlike Abiword has a problem with ttf fonts files which for some reason contain a secondary name which collides with an already installed font.

Running the font cache list command as

[FONT="Courier New"][SIZE="3"]
**fc-list : file family **| grep -i 'arial'
[/SIZE][/FONT]

as suggested at

**<[http://user.services.openoffice.ORG/en/forum/viewtopic.php?f=16&t=17373](http://user.services.openoffice.ORG/en/forum/viewtopic.php?f=16&t=17373)>**

shows the matching of font names with the ttf files and all of the entries are found as expected

eg 
[FONT="System"][SIZE="3"]
/usr/share/fonts/truetype/msttcorefonts/arialbi.ttf: Arial
/usr/share/fonts/truetype/msttcorefonts/Arial.ttf: Arial
[/SIZE][/FONT]

etc

except for this one
[FONT="System"][SIZE=3]
/usr/local/X11R6/lib/X11/fonts/truetype/misc/Alien.ttf: Alien League,Arial
[/SIZE][/FONT]

The Alien League ttf file does indeed contain the string "Arial".

So I have moved the Alien.ttf file out of the font directory tree, rerun fc-cache, and lo and behold OpenOffice now displays the correct font for Arial.

Since Abiword does not have this problem, it must be a bug in OpenOffice.  One can only hope it is fixed in the next version.

---

### Post by Corin-EU on 2009-04-18
And for those people who still want to use Alien League and keep OpenOffice working with Arial, there is a solution.

After removing your old Alien League TTF file, search the web and download the updated version

ALIEN5.TTF 

which has properly created descriptive headers and not presumably the original cut n past type affair done from an arial.ttf file.

This then shows up in fc-list as

Alien League:style=Normal,obyÄejnÃ©,Standard,ÎÎ±Î½Î¿Î½Î¹ÎºÎ¬,Regular,Normaali,NormÃ¡l,Normale,Standaard,Normalny,ÐÐ±ÑÑÐ½ÑÐ¹,Navadno,Arrunta

---


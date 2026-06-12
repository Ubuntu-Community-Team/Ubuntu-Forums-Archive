---
title: "Error: Dependency is not satisfiable: libxml1 (&gt;= 1:1.8.14-3)"
date: 2009-06-21
forum: General Help
---

### Post by Bamboozled on 2009-06-21
Hello all, 

Hopefully someone here will understand what all that goobledygook in the title means.

Like a lot of other people I have ubuntu 9.04 and a canon ip1800 printer.  Having searched for several hours on various websites, I still have no printer. Practically all the sites state to download two packages. The cnijfilter-common_2.70-2_i386.deb and cnijfilter-ip1800_2.70-2_i386-hardy.deb are on on my desktop. I cannot find a package for an ubuntu later than the hardy one.

cnijfilter-common_2.70-2_i386.deb installed by simple double clicking.

cnijfilter-ip1800_2.70-2_i386-hardy.deb is beginning to p**s me off. I double click and up comes the dreaded phrase:

Error: Dependency is not satisfiable: libxml1 (>= 1:1.8.14-3)

Who has any ideas what this means and what needs doing to retify it? I am having to keep Windows XP on the other hard drive just because I can print. 

Thanks.

Bamboozled.

---

### Post by paperplate9 on 2009-06-21
try:
sudo apt-get install libxml2

---

### Post by The-Don on 2009-06-21
If that doesn't work:
```
sudo aptitude search libxml
```

Then select one of them and use the 'install' command in place of 'search'.

---


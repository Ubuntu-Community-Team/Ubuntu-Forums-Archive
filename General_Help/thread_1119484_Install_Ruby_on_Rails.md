---
title: "Install Ruby on Rails"
date: 2009-04-08
forum: General Help
---

### Post by mdgrech on 2009-04-08
So I followed the official documentation for installing RoR here:

[https://help.ubuntu.com/community/RubyOnRails](https://help.ubuntu.com/community/RubyOnRails)

This method downloaded the rubygems to my home folder, and now in my home folder there is directory called rubygems1.3.1.  Can I hide this folder by putting a period in front it?  or even just delete it cause it looks like I already installed the gems right?

---

### Post by ibuclaw on 2009-04-08
If you plan on uninistalling RubyGems at a later date, then:
```
mv rubygems1.3.1 .rubygems1.3.1
```
Else, just remove it.

Regards
Iain

---


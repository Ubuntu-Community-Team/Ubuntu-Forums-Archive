---
title: "Problem with Ruby on Rails"
date: 2006-01-12
forum: General Help
---

### Post by rensu on 2006-01-12
Trying to install with apt-get install libbigdecimal-ruby1.8.
And getting this error:
Anyone had this error before who can help me ?:S
The following packages have unmet dependencies:
  libbigdecimal-ruby1.8: Depends: libruby1.8 (>= 1.8.1+1.8.2pre2-3) but it is not going to be installed
E: Broken packages

---

### Post by dickohead on 2006-01-17
The package: libbigdecimal-ruby1.8 needs to have libruby1.8.1 or higher, and you only have 1.8 installed, so i'd remove libruby1.8 and install something higher, then try libbigdecimal again.

---


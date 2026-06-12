---
title: "Subversion: malformed network data"
date: 2009-05-12
forum: General Help
---

### Post by dave_i_am on 2009-05-12
Ubuntu 8.04

I have working copies of subversion repositories which no
longer are able to be updated.

the command:
   svn update

yields the following error message:
  svn malformed network data

This was working several (6?) weeks ago but not now. I have
applied several Ubuntu updates in this time.


Thanks
Dave

---

### Post by exutable on 2009-05-12
I've been looking into this and it has something to do with SVN libraries not communicating properly after a server upgrade, unfortunately I didn't find a solution.

---


---
title: "help add two mime types associated with matlab"
date: 2005-10-15
forum: Desktop Environments
---

### Post by shidai.liu on 2005-10-15
Hi All,

I'm trying to add two extra mime types associated with matlab.
Matlab has .fig (matlab figure) and .mat (matlab matrix) file types. The problem lies in they have the same string at the beginning of the files look like this:

```
MATLAB 5.0 MAT-file, Platform: GLNX86, Created on: Fri Sep 23 12:42:51 2005                                             ^@
```

My question is how can I define two mime types to deal with these two file types. Now I have the following entry in /usr/share/mime/packages/freedesktop.org.xml

```
<mime-type type="application/matlab-fig">
    <comment>Matlab figure file</comment>
    <glob pattern="*.fig"/>     
    <magic priority="50">
      <match value="MATLAB 5.0 MAT-file" type="string" offset="0"/>
    </magic>
  </mime-type>
  <mime-type type="application/matlab-mat">
    <comment>Matlab data file</comment>
    <glob pattern="*.mat"/>
    <magic priority="50">
      <match value="MATLAB 5.0 MAT-file" type="string" offset="0"/>
    </magic>
  </mime-type>

```

The problem with this is .mat is also recognized as .fig file.

I've googled a lot with no avail. Your help is highly appreciated.

---

### Post by shidai.liu on 2005-10-18
Any ideas?

---


---
title: "compiz slow down: half solution."
date: 2008-12-15
forum: General Help
---

### Post by aboud on 2008-12-15
the case is compiz after random time will slow down, I red many things about this .., i came up with my own half solution..  temperarly it's helping, while i find the finial one. 

what i do is restart the compiz, after that it will work perfectly again for another round. 

to shutdown the compiz and restarted you need a script, because if you shut it down from the terminal the terminal itself will diseapper and leave you stocking. here is the script i use . 
```

kill compiz.real
compiz.real --indirect-rendering --ignore-desktop-hints --replace core ccp 

``` 

ask for more detail aboud how to write and run the script if needed. 

in case you didn't see this: 
[http://ubuntuforums.org/showthread.php?t=799070](http://ubuntuforums.org/showthread.php?t=799070)
_________________________________________________________________
vaio core 2Duo 2GB, 380MB INTEL GM965 video.

---


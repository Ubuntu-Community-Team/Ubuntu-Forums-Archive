---
title: "Batch image convert rename resize cover art for RockBox"
date: 2009-03-07
forum: General Help
---

### Post by Dithers on 2009-03-07
After looking for hours for a good way to convert/rename/resize all of my album art saved as various jpg's in subfolder after subfolder to cover.bmp I finally found a solution for the imagemagick challenged like myself!

in add/remove you will find a lovely program called Phatch
[http://photobatch.wikidot.com/getting-started](http://photobatch.wikidot.com/getting-started)

add resize batch 100 x 100
add save batch name=cover type=bmp location=<folder>/<subfolder>

and run it... make sure you check subfolders 
its very intuitive and worked great!!

---

### Post by Dithers on 2009-03-07
```

{'actions': [{'fields': {'Constrain Proportions': u'yes',
                         'Height': u'200 px',
                         'Resample Image': 'bicubic',
                         'Resolution': u'<dpi>',
                         'Scale down only': u'yes',
                         'Width': u'200 px',
                         '__enabled__': u'true'},
              'label': 'Scale'},
             {'fields': {'As': u'bmp',
                         'Filename': u'cover',
                         'In': u'<folder>/<subfolder>',
                         'JPG Quality': u'85',
                         'JPG Size Maximum': '0kb',
                         'JPG Size Tolerance': '5%',
                         'PNG Optimize': u'false',
                         'Resolution': u'<dpi>',
                         '__enabled__': u'true'},
              'label': 'Save'}],
 'description': u'Describe here the action list.'}



```

paste this into a textfile and save with a .phatch and all the settings will be correct for 200x200 bmp named cover.bmp

I upped it to 200px cux the 100x100 were all grainy must have gotten old info or for a different player

hope this helps

---


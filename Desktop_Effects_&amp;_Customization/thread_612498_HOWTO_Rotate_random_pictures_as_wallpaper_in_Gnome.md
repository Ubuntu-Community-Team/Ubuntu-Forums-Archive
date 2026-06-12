---
title: "HOWTO: Rotate random pictures as wallpaper in Gnome"
date: 2007-11-14
forum: Desktop Effects &amp; Customization
---

### Post by stuporglue on 2007-11-14
I wanted a way to randomly rotate my desktop picture in Gnome. There was a script here on the forums which randomly changed the picture between the different wallpaper files, however I wanted it to randomly pick a picture from my photo directory. 

Here's the simple version of the script. You'll need to copy/paste this somewhere executable, then add it to your Gnome Session settings to start when you log in. 

```
#!/usr/bin/perl -w
use strict;
use warnings;

my $searchPath = '~/Pictures/';   # Set to the directory you want to have searched for photos
my $switchTime = 600;               # Edit to the number of seconds between photo switches

# bgotd-- background of the day  
# Written by Michael Moore, Nov. 2007, placed in the public domain 

my @photos = `find $searchPath -type f | grep [jJ][pP][eE]*[gG]`;              
chomp(@photos);
my $photo;

while(1)
{
    $photo = $photos[rand($#photos)];
    `gconftool-2 --type string --set /desktop/gnome/background/picture_filename "$photo"`;
    sleep($switchTime);
}
```

Notes:
1) This was the initial version of the script. If you have a wide screen monitor, you'll see that portrait photos (vertical photos) don't work really well with this script. On my site, I have a slightly more complex script that uses imagemagick to combine two vertical images when needed to make a wide screen background. [http://stuporglue.org/gnome-random-wallpaper.php](http://stuporglue.org/gnome-random-wallpaper.php)

2) If lots of your images are rotated funny, install and run exifautotran, it can auto rotate images taken by most digital cameras.

3) Comments/criticisms appreciated. Especially ones that say "Here's an easier/better way to do that"

---

### Post by MNICY on 2007-11-14
Very cool.
Thread bookmarked. i will set it up sometime :D :guitar:

---

### Post by PseudoRasta on 2008-04-21
well , i went through this phase in my teens of downloading wallpapers on mass,

now that i am older i neither have the time nor inclination to do this any more  , but cant delete them all cos this would be an admission that i wasted my youth.

finding this script i a major boon .

thanks

---

### Post by signal9 on 2008-04-30
I was looking for something similar, read the articles mentioned above, then wrote my own offering.  This script reads the ~/.gnome2/backgrounds.xml file for its images, which also feeds the Change Background dialog.  Currently it is set to change backgrounds every 15 minutes.  

This can be used from the command line, or from Gnome Session Manager.

```

#!/usr/bin/env python

import gconf
import os
import random 
import time
from xml.dom.minidom import parse

class GBackground:


    def __init__ (self):
        
        self.backgroundsDB = '.gnome2/backgrounds.xml'

        self.__initGConfClient()
        self.__initDOM()

        self.__files = []

    def __initGConfClient (self):
        self.__gclient = gconf.client_get_default()

    def __initDOM (self):

        db = os.path.join( os.environ['HOME'], self.backgroundsDB )

        fh = open(db)
        self.__dom = parse(fh)
        fh.close()

    def loadBackgrounds (self):

        for wallpaper in self.__dom.getElementsByTagName('wallpaper'):

            if wallpaper.getAttribute('deleted') == 'true':
                continue

            filename = wallpaper.getElementsByTagName('filename')[0].firstChild.nodeValue
            self.__files.append(filename)

    def setRandomBackground (self):

        rnd = random.randint(0, len(self.__files) - 1)
        self.setBackground( self.__files[rnd] )

    def getBackground (self):
        return self.__gclient.get_string('/desktop/gnome/background/picture_filename')

    def setBackground (self, background):
        self.__gclient.set_string ("/desktop/gnome/background/picture_filename", background)


def main ():

    gb = GBackground()
    gb.loadBackgrounds()

    while (1):
        gb.setRandomBackground()
        time.sleep(900)


if __name__ == '__main__':
    main()

```

---

### Post by z-vap on 2008-05-01
I would love to try one of these.  But I don't store images on my PC.  Is there some method to have this automatically set an image from the web?

---

### Post by xcesarfrancox on 2008-07-20
> **z-vap said:**
> I would love to try one of these.  But I don't store images on my PC.  Is there some method to have this automatically set an image from the web?

You could try this app: [Webilder]("http://www.getdeb.net/app.php?name=Webilder")

---


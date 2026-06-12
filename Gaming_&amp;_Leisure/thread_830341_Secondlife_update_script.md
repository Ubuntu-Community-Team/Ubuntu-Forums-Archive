---
title: "Secondlife update script"
date: 2008-06-15
forum: Gaming &amp; Leisure
---

### Post by nidomedia on 2008-06-15
I created this little script which updates SecondLife to the release candidate of the client. Thought this might be of interest.

```

#!/bin/bash
# Second Life Update

mkdir -p ~/bin/programs/Secondlife

SERVER=http://release-candidate-secondlife-com.s3.amazonaws.com/
wget http://secondlife.com/support/downloads.php
FOLDERNAME=`cat downloads.php | grep -Go SecondLife_i686[^\"]*RELEASECANDIDATE | head -n1`
rm downloads.php

wget $SERVER$FOLDERNAME.tar.bz2

tar -xjvf $FOLDERNAME.tar.bz2
rm ~/bin/programs/Secondlife
mv $FOLDERNAME ~/bin/programs/Secondlife

```

I also created a gnome launcher. The command is /home/$USER/bin/programs/SecondLife/secondlife . The icon is /home/$USER/bin/programs/Secondlife/secondlife_icon.png
Replace $USER with your username, ofcourse.

Hope this is of use for somebody. If you have any suggestions for the script just let me know.

---


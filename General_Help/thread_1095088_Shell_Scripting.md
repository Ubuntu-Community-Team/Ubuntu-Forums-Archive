---
title: "Shell Scripting"
date: 2009-03-13
forum: General Help
---

### Post by 9812713 on 2009-03-13
Hello,

I know this is a broad topic, with tons of options, however I'm looking to script an command line encoder to encode files from one format to another. Here is generally what I am trying to do.

1: I have several episodes of a TV show in AVI, Mpeg and asf format, in folder /home/user/source

2: I want to encode them in ogg using ffmpeg2theora-0.23.linux64.bin

3: I want to process all the commands with the options " --audioquality 5 --channels 2 --optimize "

4: I want the output folder to be /home/user/completed

--

So far I have a script that goes like this...

```

#!/bin/sh

THEORAOPT="--audioquality 5 --channels 2 --optimize"

find -type f -name "*.*" | while read name
do
     fname=`basename $name`
     ffmpeg2theora-0.23.linux64.bin $THEORAOPT $name
done
```

Which is a  bash script I was trying to modify to do the above commands.

Can anyone help ?

Thanks.
W.

---


---
title: "Trimming electricsheep files."
date: 2009-11-29
forum: Desktop Environments
---

### Post by Barriehie on 2009-11-29
So I'm running the electricsheep screensaver and noticed that after my disk quota for the .avi files is reached the ~/.electricsheep dir is filling up with 0 length *.xxx files.  I don't see the point so I came up with this bash and gawk script to rm the *.xxx files and then remove all but 1 of the *.avi files; leaving room for fresh downloads.  sheepkiller.sh is run from my crontab file once a week; right before the backup.

crontab entry looks like this:
[color="green"]/etc/crontab[/color]
```

#
# Clean up zero length .xxx files (sheep) @ 2330 hours on Wednesday.
#
# m h dom mon dow user	command
30 23 * * 3 barrie /home/barrie/.electricsheep/sheepkiller.sh

```

[color="green"]~/.electricsheep/sheepkiller.sh[/color]
```

#!/bin/bash
##
## sheepkiller.sh
## 

WORKDIR=$HOME/.electricsheep
cd $WORKDIR

ls -1l ?????=*.??? > filez

echo '#!/bin/bash' > ./killem.sh

gawk -f ./sheepkiller.awk ./filez >> killem.sh

chmod +x ./killem.sh

./killem.sh

rm ./filez
rm ./killem.sh

#
# Nuke all but 1 of the downloaded .avi files.
#
# Specify the target directory and file names to operate on.
target_files=~/.electricsheep/*.avi
#
# Calculate the total number of files matching the target criteria. 
total_files=$(ls -t1 $target_files | wc --lines)
#
# Specify the number of files to retain.
retained_files=1
#
# If there are surplus files, delete them.
if [ $total_files -gt $retained_files ]
  then
  rm $(ls -t1 $target_files | tail --lines=$((total_files-retained_files)))
fi
#
#

exit 0

```

[color="green"]~/.electricsheep/sheepkiller.awk[/color]
```

#!/usr/bin/gawk
#
# Process the output of sheepkiller.sh to begin
# isolating the *.xxx files.
#

BEGIN { FS="//n" } {

    for ( i=1; i<=NR; i++) {

        if ( $i ~ /^?????.*\.xxx$/ ) {
            sub(/.*??:?? /, "rm /home/barrie/.electricsheep/", $i)
            print $(i)
        }

    }

}

```

Hope this helps!

Barrie

---


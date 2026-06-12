---
title: "Script to download the latest issues of FullCircleMagazine"
date: 2012-04-18
forum: Full Circle Magazine
---

### Post by CyberAngel on 2012-04-18
I just made a small script to download the latest version of the FullCircleMagazine issues (including the special editions).
What you need is to create a folder structure like this (the folder names can vary) and keep each different kind of issue on its own folder:

```
.
./Special-Editions
./Special-Editions/Scribus
./Special-Editions/Programming-Series
./Special-Editions/Programming-Series/Python
./Special-Editions/Virtualization-Series
```

Put the script in "." folder and under each subfolder download manually at least the first issue of the normal or special issues your are interested on (just the ones your are really interested).

Then run the script and it will iterate until reaching the latest uploaded issues.

```
#!/bin/bash

function download_issue {
        mydir="$1"

        pushd "$mydir" > /dev/null
        Prefix=$(ls issue* | cut -d"_" -f 1 | sed 's/issue//g' | sed 's/[0-9]*//g' | tail -1)
        Latest=$( ls issue$Prefix* | cut -d"_" -f 1 | sed 's/issue'$Prefix'//g' | sort -n | tail -1)
        echo "Latest local issue found: "$Latest""
        let "Latest += 1"
        if [ "$Prefix" == "" ]; then
                FileToDownload=issue"$Latest"_en.pdf
        else
                FileToDownload=issue"$Prefix"$(printf "%02d" $Latest)_en.pdf
        fi
        echo "Will try to download "$FileToDownload""
        wget -U Mozilla "http://dl.fullcirclemagazine.org/""$FileToDownload" 2> /dev/null
        exit_status=$?
        popd > /dev/null

        return $exit_status
}

while IFS= read -r dir; do
        filesexist=$(ls -l "$dir" | grep -v ^d | grep -v "^total [[:digit:]]" | wc -l)
        if [ $filesexist -gt 0 ]; then
                echo ""
                echo "Trying to fetch latest issues in ""$dir"
                exit_status=0
                while [ $exit_status -eq 0 ]; do
                        download_issue "$dir"
                        exit_status=$?
                        if [ $exit_status -eq 0 ]; then
                                echo "Issue "$FileToDownload" downloaded successfully"
                        else
                                echo "Issue "$FileToDownload" does not yet exist. Please check again later."
                        fi
                done
                echo ""
        fi
done < <(find . -type d)
```

---

### Post by nothingspecial on 2012-04-20
*Thread moved to **Full Circle Magazine**.*

---


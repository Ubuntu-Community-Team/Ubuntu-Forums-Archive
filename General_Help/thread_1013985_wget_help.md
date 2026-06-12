---
title: "wget help"
date: 2008-12-17
forum: General Help
---

### Post by meg23 on 2008-12-17
I want to use wget to download webpages in their entirety. Basically, I want all the images and frames to be the same as they are when viewing the site online. I looked at the manpages but I cannot seem to get what I want.

---

### Post by Linux408 on 2008-12-17
Try Downthemall pulgin for firefox [https://addons.mozilla.org/en-US/firefox/addon/201](https://addons.mozilla.org/en-US/firefox/addon/201)

I've used it to take all photos/html off a site. Can even download a whole Dir of Mp3s :P if need be

---

### Post by meg23 on 2008-12-17
I am looking for a command line utility that does this.

---

### Post by doobiest on 2008-12-17
wget --help


Recursive download:
  -r,  --recursive          specify recursive download.
  -l,  --level=NUMBER       maximum recursion depth (inf or 0 for infinite).
       --delete-after       delete files locally after downloading them.
  -k,  --convert-links      make links in downloaded HTML point to local files.
  -K,  --backup-converted   before converting file X, back up as X.orig.
  -m,  --mirror             shortcut for -N -r -l inf --no-remove-listing.
  -p,  --page-requisites    get all images, etc. needed to display HTML page.
       --strict-comments    turn on strict (SGML) handling of HTML comments.

---

### Post by ilrudie on 2008-12-17
I wrote a wget wrapper script that makes this easier.  Here it is:
```

!/usr/bin/ksh
#siteget

#check for wget
WGETBIN=/usr/bin/wget
until [[ -f $WGETBIN  ]]
do 
echo wget could not be found.  Please enter full path to wget:
read WGETBIN
done

until [[ ($ANSWERRUN = y) || ($ANSWERRUN = Y) ]]
do
    echo "Enter a url for siteget to retrieve:"
    read URL
    DOMAIN=`echo $URL | sed 's/http\:\/\///' | awk -F"/" '{printf("%s",$1)}'`
    echo $DOMAIN
    until [[ ($ANSWERDOM = y) || ($ANSWERDOM = Y) ]]
    do
        echo Domain: $DOMAIN  Is this correct"?[y/n/?]?"
        read ANSWERDOM
        if [[ ($ANSWERDOM = y) || ($ANSWERDOM = Y) ]]
            then 
            break
        elif [[ ($ANSWERDOM = n) || ($ANSWERDOM = N) ]]
            then
            echo Enter desired domain:
            read DOMAIN
        elif [[ $ANSWERDOM = ? ]]
            then
            echo Pages outside of $DOMAIN will not be downloaded.
        else
            echo Invladid selection
        fi
    done
    until [[ ($ANSWERRECURSIVE = y) || ($ANSWERRECURSIVE = Y) || ($ANSWERRECURSIVE = n) || ($ANSWERRECURSIVE = N) ]]
    do
        printf "\nRecursivly get all pages linked from this one (inside supplied domain)?[y/n]?"
        read ANSWERRECURSIVE
        if [[ ($ANSWERRECURSIVE = y ) || ($ANSWERRECURSIVE = Y ) ]]
            then
            WGETOPT="--recursive "$WGETOPT
        fi
    done

    until [[ ($ANSWERCLOBBER = y) || ($ANSWERCLOBBER = Y) || ($ANSWERCLOBBER = n) || ($ANSWERCLOBBER = N) ]]
        do
                printf "\nOverwrite existing files?[y/n]?"
                read ANSWERCLOBBER
                if [[ ($ANSWERCLOBBER = n ) || ($ANSWERCLOBBER = N ) ]]
                        then
                        WGETOPT=$WGETOPT"--no-clobber "
                fi
        done
    WGETOPT=$WGETOPT"--page-requisites --html-extension --convert-links --domains "$DOMAIN" --no-parent "
    echo Preparing to run siteget on:
    echo $URL
    echo restricted to $DOMAIN
    echo with options:
    echo $WGETOPT
    echo Is this correct? "[y/n]"
    read ANSWERRUN
done

$WGETBIN $WGETOPT $URL
exit


```This is still something I work on from time to time and its not heavily tested so let me know if you encounter errors or weird behavior so I can fix them.

---

### Post by doobiest on 2008-12-17
decent!

---


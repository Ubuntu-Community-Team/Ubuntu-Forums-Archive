---
title: "Getting ABCDE working with FLAC"
date: 2009-06-10
forum: General Help
---

### Post by ridata on 2009-06-10
I had a problem with using abcde to rip cd's into flac format, so I thought I'd post how I fixed it.

I googled it and the only thread that came up was an archived one so I couldn't post a reply there ([http://ubuntuforums.org/showthread.php?t=510213](http://ubuntuforums.org/showthread.php?t=510213)). Hopefully this moves up in the search results so people find the answer.


Anyway...
$ abcde -o flac
[ERROR] abcde: flac is not in your path.
[INFO] Define the full path to the executable if it exists on your system.

What you need to do to fix this is to run 'sudo apt-get install flac'.
The package flac works with abcde to encode your cd. Without it it can't encode to flac. The error confused me as I didn't know 'flac' was also a package. The error for ogg files will say 'vorbis-tools' isn't in your path, but that's more obviously a package.

Hope this helps someone.

---

### Post by andrew.46 on 2009-06-10
Hi ridata,

Thanks for making the effort to post this information. I see that you are using abcde from the commandline which is fair enough. An alternative is use a configuration file to create the flacs such as the following:

```

# -----------------$HOME/.abcde.conf----------------- #
# 
# A sample configuration file to convert music cds to 
#       FLAC using abcde version 2.3.99.6
# 
#       http://andrews-corner.org/abcde.html
# -------------------------------------------------- #

# Specify the encoder to use for FLAC. In this case
# flac is the only choice.
FLACENCODERSYNTAX=flac

# Specify the path to the selected encoder. In most cases the encoder
# should be in your $PATH as I illustrate below, otherwise you will 
# need to specify the full path. For example: /usr/bin/flac
FLAC=flac

# Specify your required encoding options here. Multiple options can
# be selected as '--best --another-option' etc.
FLACOPTS='--verify --best' 

# Output type for FLAC.
OUTPUTTYPE="flac"

# The cd ripping program to use. There are a few choices here: cdda2wav,
# dagrab, cddafs (Mac OS X only) and flac.
CDROMREADERSYNTAX=cdparanoia            
                                     
# Give the location of the ripping program and pass any extra options:
CDPARANOIA=cdparanoia  
CDPARANOIAOPTS="--never-skip=40"

# Give the location of the CD identification program:       
CDDISCID=cd-discid            
                               
# Give the base location here for the encoded music files.
OUTPUTDIR="$HOME/music/"               

# Decide here how you want the tracks labelled for a standard 'single-artist',
# multi-track encode and also for a multi-track, 'various-artist' encode:
OUTPUTFORMAT='${OUTPUT}/${ARTISTFILE}-${ALBUMFILE}/${TRACKNUM}.${TRACKFILE}'
VAOUTPUTFORMAT='${OUTPUT}/Various-${ALBUMFILE}/${TRACKNUM}.${ARTISTFILE}-${TRACKFILE}'

# Decide here how you want the tracks labelled for a standard 'single-artist',
# single-track encode and also for a single-track 'various-artist' encode.
# (Create a single-track encode with 'abcde -1' from the commandline.)
ONETRACKOUTPUTFORMAT='${OUTPUT}/${ARTISTFILE}-${ALBUMFILE}/${ALBUMFILE}'
VAONETRACKOUTPUTFORMAT='${OUTPUT}/Various-${ALBUMFILE}/${ALBUMFILE}'

# Put spaces in the filenames instead of the more correct underscores:
mungefilename ()
{
  echo "$@" | sed s,:,-,g | tr / _ | tr -d \'\"\?\[:cntrl:\]
}

# What extra options?
MAXPROCS=2                              # Run a few encoders simultaneously
PADTRACKS=y                             # Makes tracks 01 02 not 1 2
EXTRAVERBOSE=y                          # Useful for debugging
EJECTCD=y                               # Please eject cd when finished :-)

```

Perhaps this will be useful to you?

Andrew

---

### Post by Captain_Falafel on 2009-11-02
when I encode my CD to flac, I have them each as a different track, but I also want a cue sheet for the whole CD.. can abcde do that?

---

### Post by andrew.46 on 2009-11-03
Hi Captain,

> **Captain_Falafel said:**
> when I encode my CD to flac, I have them each as a different track, but I also want a cue sheet for the whole CD.. can abcde do that?

I believe you are after *mkcue* but I have never used this program with abcde so I am afraid that I can be of no further help with that one :(.

Andrew

---

### Post by Captain_Falafel on 2009-11-03
> **andrew.46 said:**
> Hi Captain,



I believe you are after *mkcue* but I have never used this program with abcde so I am afraid that I can be of no further help with that one :(.

Andrew


Thanks, but I tried that and just got the flac files:

```
abcde -o flac mkcue
```

---


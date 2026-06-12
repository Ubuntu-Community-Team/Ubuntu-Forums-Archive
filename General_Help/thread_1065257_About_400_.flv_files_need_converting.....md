---
title: "About 400 .flv files need converting...."
date: 2009-02-09
forum: General Help
---

### Post by Monotoko on 2009-02-09
Hiya, i have a folder with 406 .flv files in it, they are from youtube.

i know i can use ffmpeg to convert them from .flv to .mp3, thats fine, but what i really dont want to have to do is type it 406 times...........is there anyway i can automate this process?

---

### Post by hikaricore on 2009-02-09
I've never used this myself and I forget where I found it so good luck:

> #!/bin/sh
# this script should convert files from FLV to WAV and then to MP3
echo " "
echo "  Welcome to FLV to MP3 converter!  version 0.1"
echo " "
infile_name="$@"
# exit if the user did not enter anything:
if [ -z "$infile_name" ]; then
    echo " "
    echo "You did not tell me the file name, so I will exit now."
    echo " "
    exit
fi
echo " "
ffmpeg -i "$infile_name" -acodec pcm_s16le -ac 2 -ab 128k -vn -y "${infile_name%.flv}.wav"
lame --preset cd "${infile_name%.flv}.wav" "${infile_name%.flv}.mp3"
rm "${infile_name%.flv}.wav"
echo " "
echo "OK. I'm done! Have fun!"
echo " "
exit

*edit* NEVERMIND this looks like a single convertor, but what you can do is take your basic command and do as such:

> 
#!/bin/sh
export IFS=$'\n' &&  # This first line allows filenames with spaces.
for i in $(ls *.flv);
      do **COMMAND HERE**;
done


---

### Post by Monotoko on 2009-02-09
oooh that looks fun :)
allow me to try it

---

### Post by Dr Small on 2009-02-09
cd into the directory and then run:
```
for i in *; do *ffmpeg command $i*; done
```

I would suggest that you make a new directory for all the converted files, and then specify that new directory in the output location for your ffmpeg command. $i is the filename.

---

### Post by hikaricore on 2009-02-09
I guess Dr Small is assuming you have no spaces in your filenames. :p

---

### Post by Dr Small on 2009-02-09
> **hikaricore said:**
> I guess Dr Small is assuming you have no spaces in your filenames. :p
Using spaces violates section 9 of my organizing ethics. Of course I assume that he has no spaces in his file names :D

---

### Post by niteshifter on 2009-02-09
Hi,

Here's one I use. I also don't remember where I found it :)
```

#!/bin/sh

if [ -z "$1" ]; then
  echo "Usage: $0 {-divx|-xvid} list_of_flv_files"
  exit 1
fi

# video encoding bit rate
V_BITRATE=1000

while [ "$1" ]; do
  case "$1" in
    -divx)
      MENC_OPTS="-ovc lavc -lavcopts \
        vcodec=mpeg4:vbitrate=$V_BITRATE:mbd=2:v4mv:autoaspect"
      ;;
    -xvid)
      MENC_OPTS="-ovc xvid -xvidencopts bitrate=$V_BITRATE:autoaspect"
      ;;
    *)
      if file "$1" | grep -q "Macromedia Flash Video"; then
        mencoder "$1" $MENC_OPTS -vf pp=lb -oac mp3lame \
          -lameopts fast:preset=standard -o \
          "`basename $1 .flv`.avi"
      else
        echo "$1 is not Flash Video. Skipping"
      fi
      ;;
  esac
  shift
done
```

---


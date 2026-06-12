---
title: "New install is kinda slow."
date: 2006-06-30
forum: Desktop Environments
---

### Post by Flaystus on 2006-06-30
I'm very new. BAsicly have almost no clue what I'm doing.

An example to use, it took me quite a few min to figure out how to install VLC player.

Anyway I just install Xubuntu on my newly upgraded machine. Pent. D 2.66 with 1gb DDR667 and it feels kinda slow. Especially firefox when browsering and scrolling.

Is there something I can do to fix this?

---

### Post by thingy on 2006-06-30
Have you got an ATI/Nvidia graphics card?

If so, then you should follow instructions below to setup the faster versions of the ATI/Nvidia graphics card drivers, which also gives you hardware based 3d support.

How to install Graphics Driver (NVIDIA) :
[http://ubuntuguide.org/wiki/Dapper#How_to_install_Graphics_Driver_.28NVIDIA.29](http://ubuntuguide.org/wiki/Dapper#How_to_install_Graphics_Driver_.28NVIDIA.29)

How to install Graphics Driver (ATI) :
[http://ubuntuguide.org/wiki/Dapper#How_to_install_Graphics_Driver_.28ATI.29](http://ubuntuguide.org/wiki/Dapper#How_to_install_Graphics_Driver_.28ATI.29)

regards

jin

---

### Post by Flaystus on 2006-06-30
ATI but I will be switching to an nVidia in a few weeks. Should I wait?

---

### Post by Sef on 2006-06-30
> ATI but I will be switching to an nVidia in a few weeks. Should I wait?

That is entirely up to you.

---

### Post by Flaystus on 2006-06-30
Directions worked perfectly. =D>  You are a king among men.

Now if I can just find a way to stream XM.  :lol:

---

### Post by thingy on 2006-06-30
Great

I don't know what XM stands for, but see if the following helps:

Add the extra repositories (need to do this to get access to the extra software that doesn't come on the cds) :

[http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories)

Install some of the multimedia codecs:

[http://ubuntuguide.org/wiki/Dapper#How_to_install_Multimedia_Codecs](http://ubuntuguide.org/wiki/Dapper#How_to_install_Multimedia_Codecs)

Install the Windows binary only win32codecs :

[https://help.ubuntu.com/community/RestrictedFormats#head-6c942d1939d97331f96e42b63774003fde7daed5](https://help.ubuntu.com/community/RestrictedFormats#head-6c942d1939d97331f96e42b63774003fde7daed5)

Now the last step is to make sure that your app is using gstreamer as its back end. Let us know what app it is you are using to view/listen to streams.

jin

---

### Post by deathbyswiftwind on 2006-06-30
I dunno what all you need but you should check into bum (boot up manager). Since I dont own a printer I kill all of cups,hp imaging, and alot of other various tasks I dont need. It gave me a lot of extra power because I run apache and a teamspeak server ;)

---

### Post by Flaystus on 2006-06-30
thingy: Its XM Radio. Streaming version of the Sat. Service.

Sadly it uses Flash and WMP to stream. I tried to use some direction I found to load FF and Flash with Wine, but its still not working. Obviously because WMP isn't there and I don't know how to do that if its possible.

Basicly I can follow step by step directions but if I have to go alone I get lost at this point.

---

### Post by thingy on 2006-06-30
Look at this thread, 

[http://ubuntuforums.org/showthread.php?t=165490&highlight=XM+Radio](http://ubuntuforums.org/showthread.php?t=165490&highlight=XM+Radio)

and this:

[http://ubuntuforums.org/showthread.php?t=136192&highlight=XM+Radio](http://ubuntuforums.org/showthread.php?t=136192&highlight=XM+Radio)

The second one allows you to play the station using XMMS or anything else that supports listening to streaming music.

---

### Post by Flaystus on 2006-06-30
None of that seems to work. But I did find this.

[https://launchpad.net/distros/ubuntu/+ticket/115](https://launchpad.net/distros/ubuntu/+ticket/115)

But I have no idea what to call the file they want you to make or what to do with it. :confused:


edit: well figured out to to make it a script and run it but it gives an error parsing HTML.

oh well...

---

### Post by thingy on 2006-06-30
What you need to do is copy the contents of the quote below, into gedit and save the file as xmonline.sh

Before you save the file, you need to edit the file to change the USER="USER" and PASS="PASS" lines to your own user name and password.

Also, the PLAYER=filename line should be set to what player you want to use.

Then in the terminal, goto the directory you saved the file in and type in "chmod a+rx xmonline.sh" which will make the file executable.

Now to listen to XM Radio, you simply need to type in "./xmonline.sh 22" <-- where 22 is the channel number.

I'll try this when I get home tonight to see if it works.

Here's the script from that URL:

> 
#!/bin/bash
# You must do: chmod a+rx xmonline.sh
# before you can run this script
# usage: ./xmonline.sh 22`
# usage: xine `xmonline.sh 22`
# Thanks to B. Galliart

# Please set the following variables
# The script will only work with a valid XM Online USER and PASS
USER="USER"
PASS="PASS"
CHAN=$1
RATE="high" # setting for the bit RATE are "low" or "high"
PLAYER="totem"
# PLAYER="mplayer"
# PLAYER="alsaplayer"
# PLAYER="xmms"
# Set NO SONG INFO below to 1 to skip getting updates on the song playing
NOSONGINFO=0
UPDATEDELAY=5

### You should not need to modify anything beyond this point

if [ "x$USER" == "xUSER" ] ; then
echo You must modify the USER variable in the script >&2
exit 1
fi

if [ "x$PASS" == "xPASS" ] ; then
echo You must modify the PASS variable in the script >&2
exit 1
fi

if [ "x$CHAN" == "x" ] ; then
echo Must provide a channel number on the command line >&2
echo Such as \"$0 22\" to play channel 22 >&2
exit 1
fi

if [ ! -d $HOME/.xmonline ] ; then
mkdir $HOME/.xmonline
fi

cd $HOME/.xmonline

rm -f xmonline.cookies xmonlinelogin.out xmonlinestream.out \
xmonlinesong.out xmonlinesong.old
curl -s -c xmonline.cookies -d "user_id=$USER" -d "pword=$PASS" \
[http://xmro.xmradio.com/xstream/login_servlet.jsp](http://xmro.xmradio.com/xstream/login_servlet.jsp) > xmonlinelogin.out
EXITCODE=$?
if [ $EXITCODE -ne 0 ] ; then
echo curl error exit value $EXITCODE >&2
exit $EXITCODE
fi

egrep "Invalid email and/or password" xmonlinelogin.out > /dev/null
if [ $? -eq 0 ] ; then
echo Invalid email and/or password >&2
exit 1
fi

egrep "[(]Not .*? " xmonlinelogin.out > /dev/null
if [ $? -eq 0 ] ; then
echo -n "Logged in as: " >&2
egrep "[(]Not .*? " xmonlinelogin.out | \
sed 's/.*[(]Not //;s/? .*//' >&2
fi
rm -f xmonlinelogin.out

curl -s -b xmonline.cookies -d "" \
"http://player.xmradio.com/player/2ft/playMedia.jsp?ch=$CHAN&speed=$RATE" \
> xmonlinestream.out
egrep "xmmediaplayer[.]URL = '" xmonlinestream.out > /dev/null
if [ $? -eq 0 ] ; then
STREAM=`egrep "xmmediaplayer[.]URL = '" xmonlinestream.out | \
sed "s/.*xmmediaplayer[.]URL = '//;s/';.*//"`
else
egrep "<PARAM NAME=\"FileName\" VALUE=\"" xmonlinestream.out > /dev/null
if [ $? -eq 0 ] ; then
STREAM=`egrep "<PARAM NAME=\"FileName\" VALUE=\"" xmonlinestream.out | \
sed "s/.*<PARAM NAME=\"FileName\" VALUE=\"//;s/\">.*//"`
else
echo "Error parsing html to find stream URL" >&2
exit 1
fi
fi
rm -f xmonlinestream.out
echo Stream URL $STREAM >&2

$PLAYER $STREAM &
PLAYERPID=$!

if [ $NOSONGINFO -eq 1 ] ; then
exit 0
fi

while [ true ] ; do
curl -s -b xmonline.cookies -d "" -H "Pragma: no-cache" \
"http://player.xmradio.com/padData/pad_data_servlet.jsp?channel=$CHAN&rnd=$RANDOM" \
> xmonlinesong.out
egrep "<artist>|<album>|<songtitle>|<channelnumber>|<channelname>" \
xmonlinesong.out > /dev/null
if [ $? -ne 0 ] ; then
echo "Error parsing html to find song info" >&2
exit 1
fi
if [ -f xmonlinesong.old ] ; then
DIFF=`comm -3 xmonlinesong.out xmonlinesong.old | wc -l`
else
DIFF=1
fi
if [ $DIFF -gt 0 ] ; then
egrep "<artist>|<album>|<songtitle>|<channelnumber>|<channelname>" \
xmonlinesong.out | sed 's/<\/[a-z]*>//' | \
sed 's/^..<artist>/ Artist: /' | \
sed 's/^..<album>/ Album: /' | \
sed 's/^..<songtitle>/ Song Title: /' | \
sed 's/^..<channelnumber>/ Channel #: /' | \
sed 's/^..<channelname>/ Channel Name: /' >&2
echo
fi
sleep $UPDATEDELAY
mv xmonlinesong.out xmonlinesong.old
( kill -0 $PLAYERPID 2>&1 ) > /dev/null
if [ $? -eq 1 ] ; then
echo Player ended >&2
rm -f xmonlinesong.old
exit 0
fi
done


---

### Post by Flaystus on 2006-06-30
Thanks for the help thingy. I did eventually figure out to do that but then my system problem distracted me.

Sadly it seems that script needs to be updated or something because it gives some sort of HTML parsing error when I use it.

The sad part is I don't even want the track info, I Just want to listen to Opie and Anthony in the morning.

---


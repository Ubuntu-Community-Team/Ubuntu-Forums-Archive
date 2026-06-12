---
title: "use conky to display Torrentflux stats"
date: 2008-12-28
forum: General Help
---

### Post by markp1989 on 2008-12-28
I have just started a small script that can be called by conky to show stats of currently running torrents. 

currently it outputs:
Torrent title (removes puncuation and makes it all upper case )
estimated time / stoped / completed / waiting / connecting to peers
TX Speed (per torrent) 
RX Speed (per torrent) 

script : I placed my script in ~/scripts

```
dir=/media/downloads ## specify download dir 
cutno=30 #Specifies the number of characters to show in the title name, usefull to stop long torrent names from stretching conky
cd $dir/.torrents
echo Transfers: `ls *.stat  | wc -l`
echo " "
for file in *.stat; do
echo $file | cut -f1 -d'.' | cut -c 1-$cutno | tr '_' ' ' | tr -d '[{}(),\!]' | tr -d "\'" | tr '[A-Z]' '[a-z]';  ##Displays torrent name, without puncuation
	echo `cat $file | head -n 3 | tail -n 1;` : `cat $file | head -n 2 | tail -n 1;`% ##displays the current status of the torrent
	echo RX speed: `cat $file |  head -n 4 | tail -n 1;` ##displays the downspeed 
	echo TX speed: `cat $file |  head -n 5 | tail -n 1;` ##displays the upspeed
        echo Seeds: `cat $file |  head -n 7 | tail -n 1 | cut -f1 -d'+';` ##displays the amount of seeds 
        echo Peers: `cat $file |  head -n 8 | tail -n 1 ;` ##displays the amount of peers
	echo " "

done
```
here is my conky rc 
```
background yes

use_xft yes
# xft font when Xft is enabled
xftfont LucidaMacBold:size=7
override_utf8_locale yes

# Text alpha when using Xft
xftalpha 1

update_interval 1
draw_shades no
draw_outline yes
draw_borders no
stippled_borders no
border_margin 0
border_width 1
default_color BFFFB7 #3FB2C1 #CFE5D3 #BFFFB7 #B1B1B1 #FF8086 #61FFE2 #7EFFF7 #7EB6FF #BAF5FF #BFFFB7 #FFF2E6 #9DFFDD #B599FF 
default_shade_color ffffff
default_outline_color 303030
own_window yes
own_window_transparent no
own_window_type widget
own_window_hints undecorate,sticky,skip_taskbar,skip_pager,below
own_window_colour 121212
alignment top_left
gap_x 0
gap_y 0
no_buffers yes
uppercase no
double_buffer yes
use_spacer none
minimum_size 20 0
mail_spool $HOME/Maildir/

#${rss http://www.abc.net.au/news/indexes/idx-australia/rss.xml 60 feed_title}

TEXT
${font LucidaGrande:size=10}${color ffffff}Current Downloads
${font}${execi 10 /home/mark/scripts/torrentstats.sh}
```
here is a screen shot of my conky. 

[IMG]http://i246.photobucket.com/albums/gg102/markp1989/2008-12-30-201726_2880x900_scrot.png[/IMG]
as u can see my ISP throttle my torrernt traffic (the main reason i want to monitor it constantly), hence the slow downloads 

any thing that doesnt seem right, tell me and i will see what i can do. 

I am planing to add extra features to it, such as total download / upload soonish.

PS if this is the wrong section, please move it.

---

### Post by markp1989 on 2008-12-30
would someone be willing to tell me how to add the outputs of 
```
cat $file |  head -n 4 | tail -n 1 | tr 'a-z' ' ' | tr 'A-Z' ' ' | tr '/' ' '; ##rx speed 
```
together to i can display the total download speed?

thanks. markp1989

---

### Post by markp1989 on 2009-01-15
Made a few changes to the script

currently it outputs:
Total RX speed  ** curl is required**
Total TX speed ** curl is required**
Free Space ** curl is required**
Running torrents 
Torrent title (removes puncuation and makes it all upper case )
estimated time / stoped / completed / waiting / connecting to peers - percent complete 
TX Speed (per torrent)
RX Speed (per torrent)

```
#!/bin/bash
dir=/media/torrents ## replace with torrentflux download dir can be on this computer, or mounted over nfs
cutno=30 #Specifies the number of characters to show in the title name, usefull to stop
host=127.0.0.1/torrentflux ## the address of your torrent flux instalation, can be local host or remote host. 
user=******
pass=******

curl -c .tf_cookie -d username=$user -d iamhim=$pass $host/login.php >/dev/null 2>&1 ##creates a hidden cookie file
curl -H "Expect:" -b .tf_cookie $host/index.php  >/dev/null 2>&1 > .torrentstats.tmp  # uses curl to dump the torrent page to a hidden file 

echo Down Speed `cat .torrentstats.tmp | grep -i '<strong' | tail -n 4| head -n 1 | cut -f3 -d'>' | cut -f1 -d'<';` #Total down 
echo Up Speed `cat .torrentstats.tmp | grep -i '<strong' | tail -n 3| head -n 1 | cut -f3 -d'>' | cut -f1 -d'<';`     # Total up
echo Free Space `cat .torrentstats.tmp | grep -i '<strong' | tail -n 2| head -n 1 | cut -f3 -d'>' | cut -f1 -d'<';`   # remaining space 

cd $dir/.torrents
echo Transfers: `ls *.stat  | wc -l` ##counts the amount transfers
echo " "
for file in *.stat; do
size=`cat $file | tail -n 1;`
echo $file | cut -f1 -d'.' | cut -c 1-$cutno | tr '_' ' ' | tr -d '[{}(),\!]' | tr -d "\'" | tr '[a-z]' '[A-Z]'; ## displays torrent names
echo `cat $file | head -n 3 | tail -n 1 | tr '[a-z]' '[A-Z]';`  : `cat $file | head -n 2 | tail -n 1;`% ## displays the status
echo RX speed: `cat $file |  head -n 4 | tail -n 1;`  ##displays the current download speed per torrent
echo TX speed: `cat $file |  head -n 5 | tail -n 1;` ##displays the current upload speed per torrent
echo size: `expr $size / 1048576` MB ##displays the file size
echo Seeds: `cat $file |  head -n 7 | tail -n 1 | cut -f1 -d'+';` ##displays the amount of seeds
echo Peers: `cat $file |  head -n 8 | tail -n 1 ;` ##displays the amount of peers
echo " "
done

```

screen
[IMG]http://i246.photobucket.com/albums/gg102/markp1989/2009-01-15-182409_2880x900_scrot.png[/img]

Any feed back will be appriciated.

---

### Post by markp1989 on 2009-02-07
After i gave my sister an account on my torrentslave. when she added torrents it would clutter up my conky. so i changed the script to only show torrents for the user that the script uses to login. 

```
#!/bin/dash
dir=/media/downloads ## replace with torrentflux download dir
cutno=26 #Specifies the number of characters to show in the title name
host=http://192.168.1.99/torrentflux
user=mark
pass=*****

rm .tf_cookie
curl -c .tf_cookie -d username=$user -d iamhim=$pass $host/login.php >/dev/null 2>&1
curl -H "Expect:" -b .tf_cookie $host/index.php  >/dev/null 2>&1 > .torrentstats.tmp

echo RX Speed `cat .torrentstats.tmp | grep -i '<strong' | tail -n 4| head -n 1 | cut -f3 -d'>' | cut -f1 -d'<';` Kb/s
echo TX Speed `cat .torrentstats.tmp | grep -i '<strong' | tail -n 3| head -n 1 | cut -f3 -d'>' | cut -f1 -d'<';` Kb/s
echo Free Space `cat .torrentstats.tmp | grep -i '<strong' | tail -n 2| head -n 1 | cut -f3 -d'>' | cut -f1 -d'<';`

cd $dir/.torrents
echo Transfers: `ls *.stat  | wc -l` ##counts the amount transfers 
echo " "
for file in *.stat; do
if cat $file | grep -qw $user; then 
size=`cat $file | tail -n 1;`
echo $file | cut -f1 -d'.' | cut -c 1-$cutno | tr '_' ' ' | tr -d '[{}(),\!]' | tr -d "\'" | tr '[a-z]' '[A-Z]'; ## displays torrent names, in upper case, without any puncuation 
echo `cat $file | head -n 3 | tail -n 1 | tr '[a-z]' '[A-Z]';`  : `cat $file | head -n 2 | tail -n 1;`% ## displays the status of the torrent
echo RX speed: `cat $file |  head -n 4 | tail -n 1;`  ##displays the current download speed per torrent 
echo TX speed: `cat $file |  head -n 5 | tail -n 1;` ##displays the current upload speed per torrent 
echo size: `expr $size / 1048576` MB ##displays the file size 
echo Seeds: `cat $file |  head -n 7 | tail -n 1 | cut -f1 -d'+';` ##displays the amount of seeds 
echo Peers: `cat $file |  head -n 8 | tail -n 1 ;` ##displays the amount of peers
echo " "
else 
echo "not mine" >/dev/null
fi 
done

```

---

### Post by markp1989 on 2009-03-15
bump

any one using this with success or problems?

edit: i will be altering this script to fix all the "cat | grep" to make it cleaner, and lighter

---

### Post by markp1989 on 2009-03-15
Changes: 

changed all incorect "cat $file | grep" to "grep $file" which should save a little bit of resorces. 

fixed the size line, so that if there are errors on the download, it doesnt give an expr error in the size feild. 


```
#!/bin/dash
dir=/media/downloads ## replace with torrentflux download dir
cutno=26 #Specifies the number of characters to show in the title name
host=http://192.168.1.99/torrentflux
user=mark
pass=*****

rm .tf_cookie
curl -c .tf_cookie -d username=$user -d iamhim=$pass $host/login.php >/dev/null 2>&1
curl -H "Expect:" -b .tf_cookie $host/index.php  >/dev/null 2>&1 > .torrentstats.tmp

echo RX Speed `grep -i '<strong' .torrentstats.tmp | tail -n 4| head -n 1 | cut -f3 -d'>' | cut -f1 -d'<';` Kb/s
echo TX Speed `grep -i '<strong' .torrentstats.tmp | tail -n 3| head -n 1 | cut -f3 -d'>' | cut -f1 -d'<';` Kb/s
echo Free Space `grep -i '<strong' .torrentstats.tmp | tail -n 2| head -n 1 | cut -f3 -d'>' | cut -f1 -d'<';`

cd $dir/.torrents
echo Transfers: `ls *.stat  | wc -l` ##counts the amount transfers 
echo " "
for file in *.stat; do
if grep -qw $user $file ; then 
size=`head -n 13 $file | tail -n 1;`
echo $file | cut -f1 -d'.' | cut -c 1-$cutno | tr '_' ' ' | tr -d '[{}(),\!]' | tr -d "\'" | tr '[a-z]' '[A-Z]'; ## displays torrent names, in upper case, without any puncuation 
echo `head -n 3 $file | tail -n 1 | tr '[a-z]' '[A-Z]';`  : `cat $file | head -n 2 | tail -n 1;`% ## displays the status of the torrent
echo RX speed: `head -n 4 $file | tail -n 1;`  ##displays the current download speed per torrent 
echo TX speed: `head -n 5 $file | tail -n 1;` ##displays the current upload speed per torrent 
echo size: `expr $size / 1048576` MB ##displays the file size 
echo Seeds: `head -n 7 $file | tail -n 1 | cut -f1 -d'+';` ##displays the amount of seeds 
echo Peers: `head -n 8 $file| tail -n 1 ;` ##displays the amount of peers
echo " "
else 
echo "not mine" >/dev/null
fi 
done
```

---

### Post by globalenigma on 2009-05-25
I really like this idea... But it is not working for me.  It shows my RX / TX speed and Free space but that is all... Any ideas?

---

### Post by markp1989 on 2009-05-25
> **globalenigma said:**
> I really like this idea... But it is not working for me.  It shows my RX / TX speed and Free space but that is all... Any ideas?

the dir line needs to be set. 

are you running the conky on the same pc as torrentflux? or on a different pc?

If its on a different pc, like my setup, you need to mount the download dir using nfs or somthing similar. 

also, can you just run the script in the terminal, that way you will be able to see any errors

---

### Post by markp1989 on 2009-05-31
> **globalenigma said:**
> I really like this idea... But it is not working for me.  It shows my RX / TX speed and Free space but that is all... Any ideas?

you had any luck?

---

### Post by Toky on 2009-06-04
This sounds cool, I will give it a shot with my torrentflux-b4rt
My torrentflux lives in my GW/FW, separate from the desktops in my house.

---

### Post by xjgnsdof on 2009-09-20
It doesn't work with Torrentflux-b4rt. It displays "835.93 GB KB/s" at the end as my RX speed, which is obviously a bug.

---

### Post by markp1989 on 2009-09-20
> **elgilicious said:**
> It doesn't work with Torrentflux-b4rt. It displays "835.93 GB KB/s" at the end as my RX speed, which is obviously a bug.

I dont have torrrentflux-b4rt on any systems i have, would you be able to send me the .torrentstats.tmp file that would be in the folder you ran the script from so i can see how that file differs from the original torrentflux file?

---

### Post by onemyndseye on 2009-12-15
It would be easier for you to call stats.php and parse that list for your data:

Example: (Note no transfers running)
```

~$ curl "http://myhost/torrentflux/stats.php?t=all&f=xml&username=MYUSER&iamhim=MYPASSWD"

<?xml version="1.0" encoding="utf-8"?>
<tfbstats>
 <server>
  <serverStat name="speedDown">0.00</serverStat>
  <serverStat name="speedUp">0.00</serverStat>
  <serverStat name="speedTotal">0.00</serverStat>
  <serverStat name="cons">0</serverStat>
  <serverStat name="freeSpace">248.80 GB</serverStat>
  <serverStat name="loadavg">0.23</serverStat>
  <serverStat name="running">0</serverStat>
  <serverStat name="queued">0</serverStat>
  <serverStat name="speedDownPercent">0</serverStat>
  <serverStat name="speedUpPercent">0</serverStat>
  <serverStat name="driveSpacePercent">86</serverStat>
 </server>
 <xfer>
  <xferStat name="xferGlobalTotal">208.03 GB</xferStat>
  <xferStat name="xferGlobalMonth">34.58 GB</xferStat>
  <xferStat name="xferGlobalWeek">7.58 GB</xferStat>
  <xferStat name="xferGlobalDay">0.00 MB</xferStat>
  <xferStat name="xferUserTotal">208.03 GB</xferStat>
  <xferStat name="xferUserMonth">34.58 GB</xferStat>
  <xferStat name="xferUserWeek">7.58 GB</xferStat>
  <xferStat name="xferUserDay">0.00 MB</xferStat>
 </xfer>
 <users>
  <user name="onemyndseye">
   <userProp name="state">online</userProp>
  </user>
 </users>
 <transfers>
 </transfers>
</tfbstats>

```

Or in text format: (1 transfer running)
```

~$ curl "http://myhost/torrentflux/stats.php?t=all&f=txt&username=MYUSER&iamhim=MYPASS"
1.20;0.00;1.20;2;248.80 GB;0.15;1;0;0;0;86
208.04 GB;34.59 GB;7.58 GB;2.17 MB;208.04 GB;34.59 GB;7.58 GB;2.17 MB
onemyndseye;online
myfile.torrent;15.9 MB;Leeching;13.5%;1.2 kB/s;0.0 kB/s;03:07:54

```

Or even RSS format  (With a added user + 1 transfer)
```

~$ curl "http://myhost/torrentflux/stats.php?t=all&f=rss&username=MYUSER&iamhim=MYPASS"
<?xml version='1.0' ?>

<rss version="0.91">
 <channel>
  <title>torrentflux Stats</title>
   <item>
    <title>Server Stats</title>
    <description>Speed Down: 8.70 || Speed Up: 0.00 || Speed Total: 8.70 || Connections: 3 || Free Space: 248.79 GB || Load: 0.26 || Running: 1 || Queued: 0 || Speed Down (Percent): 1 || Speed Up (Percent): 0 || Drive Space (Percent): 86    </description>
   </item>
   <item>
    <title>Xfer Stats</title>
    <description>Server : Total Transfer: 208.04 GB || Server : Month's Transfer: 34.59 GB || Server : Week's Transfer: 7.58 GB || Server : Today's Transfer: 4.70 MB || User : Total Transfer: 208.04 GB || User : Month's Transfer: 34.59 GB || User : Week's Transfer: 7.58 GB || User : Today's Transfer: 4.70 MB    </description>
   </item>
   <item>
    <title>Users</title>
    <description>crash: offline || onemyndseye: online    </description>
   </item>
   <item>
    <title>Transfer: myfile.torrent</title>
    <description>Size: 15.9 MB || Status: Leeching || Progress: 29.5% || Down: 8.7 kB/s || Up: 0.0 kB/s || Estimated Time: 21:52    </description>
   </item>
 </channel>
</rss>

```


Here is the usage guide for stats.php
```

Params :

"t" : type : optional, default is "all"
      "all"        : server + xfer + transfers + users
      "server"     : server-stats
      "xfer"       : xfer-stats
      "users"      : users-stats
      "transfers"  : transfer-stats
      "transfer"   : transfer-stats of a single transfer. needs extra-param "i" with the name of the transfer
"f" : format : optional, default is "xml"
      "xml"        : new xml-formats, see xml-schemas in dir "xml"
      "rss"        : rss 0.91
      "txt"        : csv-formatted text
"h" : header : optional, only used in txt-format, default is "0"
      "0"          : send header
      "1"          : dont send header.
"a" : send as attachment : optional, default is "0"
      "0"          : dont send as attachment
      "1"          : send as attachment
"c" : send compressed (deflate) : optional, default is "0"
      "0"          : dont send compressed
      "1"          : send compressed (deflate)

Examples :

* http://mythtv/torrentflux/stats.php?t=all&f=xml              :  all stats sent as xml
* http://mythtv/torrentflux/stats.php?t=server&f=xml&a=1       :  server stats as xml sent as attachment
* http://mythtv/torrentflux/stats.php?t=transfers&f=xml&c=1    :  transfer stats as xml sent compressed
* http://mythtv/torrentflux/stats.php?t=all&f=rss              :  all stats sent as rss
* http://mythtv/torrentflux/stats.php?t=all&f=txt&h=0          :  all stats sent as txt without headers
* http://mythtv/torrentflux/stats.php?t=xfer&f=txt&a=1&c=1     :  xfer stats as text sent as compressed attachment

* http://mythtv/torrentflux/stats.php?t=transfer&i=foo.torrent        :  transfer-stats of foo sent in default-format
* http://mythtv/torrentflux/stats.php?t=transfer&i=bar.torrent&f=xml  :  transfer-stats of bar sent as xml

* http://mythtv/torrentflux/stats.php?t=all&f=xml&username=admin&iamhim=seceret                            :  all stats sent as xml. use auth-credentials "admin/seceret"
* http://mythtv/torrentflux/stats.php?t=all&f=rss&username=admin&md5pass=dc5c74cfa3ba35eb87cf597a60fa756c  :  all stats sent as rss. use auth-credentials "admin/dc5c74cfa3ba35eb87cf597a60fa756c"


```


In my eyes it would be easiest to make a seperate call to each section that you want:
```

curl "http://myhost/torrentflux/stats.php?t=server&f=rss&username=MYUSER&iamhim=MYPASS"  > tmp1
curl "http://myhost/torrentflux/stats.php?t=xfer&f=rss&username=MYUSER&iamhim=MYPASS"    > tmp2 
curl "http://myhost/torrentflux/stats.php?t=users&f=rss&username=MYUSER&iamhim=MYPASS"   > tmp3
curl "http://myhost/torrentflux/stats.php?t=transfers&f=rss&username=MYUSER&iamhim=MYPASS" > tmp4

```

Then mangle each section into the format you wish and output into a combined file:
```

cat tmp1 |grep blah| sed '{s/blah/blah/g}' >output
cat tmp2 |grep blah| sed '{s/blah/blah/g}' >>output
cat tmp3 |grep blah| sed '{s/blah/blah/g}' >>output
cat tmp4 |grep blah| sed '{s/blah/blah/g}' >>output

# display it
cat output

#clean up
rm tmp1 tmp2 tmp3 tmp4 output

```

You can use your cookie method to keep from sending user/pass on each connect if you like.
Hope this helps,
-onemyndseye

---

### Post by onemyndseye on 2009-12-15
Heres a quick exmaple of using sed to parse xml. Will parse the xml dump and print evertying between the <transfers> tags
```

curl -s "http://myhost/torrentflux/stats.php?t=all&f=xml&username=MYUSER&iamhim=MYPASS" > ./output
cat ./output | sed -n '/<transfers>/,/<\/transfers>/p'

# Output
<transfers>
 <transfer name="myfile.torrent">
  <transferStat name="Size">15.9 MB</transferStat>
  <transferStat name="Status">Seeding</transferStat>
  <transferStat name="Progress">0.00%</transferStat>
  <transferStat name="Down">0.0 kB/s</transferStat>
  <transferStat name="Up">0.0 kB/s</transferStat>
  <transferStat name="Estimated Time">-</transferStat>
 </transfer>
</transfers>

# Then can remove the <tags>
cat ./output | sed '{s/<[^>]*>//g}'


# Output
   15.9 MB
   Seeding
   0.00%
   0.0 kB/s
   0.0 kB/s
   -

# Or all in one
cat ./output | sed -n '/<transfers>/,/<\/transfers>/p' | sed '{s/<[^>]*>//g}'


```

RSS should work nearly the same way and might even be abit easier to manage..  That should get you started mangling the output as needed :)  This method will work for any version of torrentflux*


*** EDIT:

Quick and dirty readable format via RSS
```

#!/bin/bash

TF_STATS=http://myhost/torrentflux/stats.php
USER=onemyndseye
PASS=mypassword
CURL="$(which curl) -s"


${CURL} "${TF_STATS}?t=all&f=rss&username=${USER}&iamhim=${PASS}" | sed '{s/|| /\n/g;s/<[^>]*>//g;s/^[ \t]*//;s/[ \t]*$//;/./,$!d}'


```


There is afew different ways you could go about filter for a specific users torrents.  My suggestion would be to change to torrentflux-b4rt as it has this option built in.

---

### Post by onemyndseye on 2009-12-16
If you are still interested in filtering for a users torrents I will share my own script.  It doesnt have this function but has the stepping stones to get you there ;)


tf-stats.sh
```

#!/bin/bash

##################### Settings #################
TF_USER=myuser
PASS=mypassword
TF_HOST=myhost
TF_PATH=/torrentflux
TF_COOKIE=~/.tf_cookie
#################### END Settings ##############
do_login() {

# do Login and create cookie
curl -s -c $TF_COOKIE -d username=$TF_USER -d iamhim=$PASS http://${TF_HOST}${TF_PATH}/login.php >/dev/null 2>&1
}

get_user_dir() {
CURL="$(which curl) -s -H "Expect:" -b $TF_COOKIE"
TF_DIRS="http://${TF_HOST}${TF_PATH}/index.php?iid=dir&dir=${TF_USER}" 

${CURL} "${TF_DIRS}" |grep "<a href=\"\index.php?iid=dir&"|grep -v "index.php?iid=dir&chmod"| sed '{s/<[^>]*>//g; s/^[ \t]*//;s/[ \t]*$//;/./,$!d }'|sed '/^$/d'
}

get_stats() {
TYPE=$1

TF_STATS=http://${TF_HOST}${TF_PATH}/stats.php
CURL="$(which curl) -s -H "Expect:" -b $TF_COOKIE"
${CURL} "${TF_STATS}?t=${TYPE}&f=rss&username=${USER}&iamhim=${PASS}" | sed '{s/|| /\n/g;s/<[^>]*>//g;s/^[ \t]*//;s/[ \t]*$//;/./,$!d}'
}

display_stats() {

TMP1=$(cat $stats1 |grep -c "")
if [ $TMP1 -lt 5 ]; then
  echo "Error reading stats from $TF_STATS"
  echo ""
  echo "The output was:"
  cat $stats1
  exit 1
fi


cat <<EOF  
--------------------------------------------
Server stats
--------------------------------------------
$(cat $stats1 | grep -A 11 "Server Stats" |grep -v "Server Stats")

--------------------------------------------
Transfer stats
--------------------------------------------
Server :: 
$(cat $stats1 |grep "Server :" | sed '{s/Server : /        /g}')

User   ::
$(cat $stats1 |grep "User :" | sed '{s/User : /        /g}')

--------------------------------------------
Users
--------------------------------------------
$(cat $stats1 |grep ": online")
$(cat $stats1 |grep ": offline")

--------------------------------------------
Transfers
--------------------------------------------
$(cat $stats2 |grep -v "torrentflux Stats" | sed '{s/[ \t]*$//;/./,$!d}')


--------------------------------------------
File List
--------------------------------------------
$(get_user_dir)

EOF
}

stats1=$(mktemp)
stats2=$(mktemp)
get_stats all >$stats1
get_stats transfers >$stats2

case "$1" in 
       -gui)
            [ ! -f "$TF_COOKIE" ] && do_login
            display_stats | zenity --text-info --title "Torrentflux stats for: $TF_HOST" 
            ;;
       -txt)
            echo "--------------------------------------------"
            echo "Torrentflux stats for: $TF_HOST"
            echo "--------------------------------------------"
            [ ! -f "$TF_COOKIE" ] && do_login
            display_stats 
            ;;
          *)
            echo "--------------------------------------------"
            echo "Torrentflux stats for: $TF_HOST"
            echo "--------------------------------------------"
            [ ! -f "$TF_COOKIE" ] && do_login
            display_stats
            ;;
esac

rm $stats1 $stats2
exit 0

```

the scripts usage is:
    tf-stats.sh 
    tf-stats.sh -txt (output in txt format *This is default)
    tf-stats.sh -gui (output to a GUI dialog box)



the get_user_dir() function parses the HTML output from your personal dir link in Torrentflux.  Using the info gathered here is the 1st step to filtering your list.

it could be called to set a variable for instance:
```

MY_FILES="$(get_user_dir)"

```

then using a `for` statement you could start your filtering.
```

# This may need a modified IFS=
for I in $MY_FILES; do
  # somehow compare I (each file name) to the list of transfers
  blah blah
done

```


This concludes my needs in this project.   I hope some of these peices help you.  Feel free to give a shout if you need anything further.

-onemyndsye

---


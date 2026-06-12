---
title: "gnome-terminal - segfault"
date: 2014-05-15
forum: Desktop Environments
---

### Post by sven8 on 2014-05-15
Hi Ubuntu community

first of all, sorry for my englisch, i hope u understand my problem.

I have a script which connets to alle our servers, and collects informations.
whit this infomration i make severals new gnome-terminal profiles whit a script.

after it im able to use some kind of "jump" function which chooses the right termina-profile which, does automatic a ssh connection to the server saved on the gnome-profile.

This all works perfect and makes my daily work much faster.
but sometimes (i did not figure out why) all gnome-terminals are segfaulting to the same time.
it does not matter if i am doing somthing in ubuntu or in the terminal or it is  just idle.

i found the fallwoing in the kernel.log

```

May 14 11:11:54 w048mi kernel: [41735.337086] show_signal_msg: 153 callbacks suppressed
May 14 11:11:54 w048mi kernel: [41735.337101] gnome-terminal[2368]: segfault at 28 ip 00007fd7a18a2ccd sp 00007fff89444f70 error 4 in libgtk-3.so.0.1000.8[7fd7a17d8000+4ff000]

```

thats all i figured out. i cant send the error report to ubuntu, because we are not allowed to connect with linux to the internet (they say its not secure :D )

Environment
VMWare 5.0.1
Ubuntu: Linux w048mi 3.13.0-24-generic #47-Ubuntu SMP Fri May 2 23:30:00 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

thx for any help u can give me

---

### Post by konnn2 on 2014-05-15
It might be helpful if you gave the script so someone may find a fault in that.

---

### Post by sven8 on 2014-05-16
this is true. I wont post the script, because i guess no one will understand what i did (im not good in scripting) :D

But here is my gnome-terminal profiel (1 for each server)

cat /home/laubersv/.gconf/apps/gnome-terminal/profiles/h054r7/%gconf.xml

```
<?xml version="1.0"?>
<gconf>
 <entry name="scroll_on_keystroke" mtime="1400166548" type="bool" value="false"/>
 <entry name="bold_color_same_as_fg" mtime="1399646356" type="bool" value="true"/>
 <entry name="use_theme_colors" mtime="1400166548" type="bool" value="false"/>
 <entry name="exit_action" mtime="1400166548" type="string">
  <stringvalue>hold</stringvalue>
 </entry>
 <entry name="silent_bell" mtime="1400166548" type="bool" value="true"/>
 <entry name="default_show_menubar" mtime="1400166548" type="bool" value="false"/>
 <entry name="allow_bold" mtime="1400166548" type="bool" value="false"/>
 <entry name="use_theme_background" mtime="1399646356" type="bool" value="false"/>
 <entry name="use_custom_command" mtime="1400166548" type="bool" value="true"/>
 <entry name="custom_command" mtime="1400166548" type="string">
  <stringvalue>ssh -t hnix1a ssh h054r7</stringvalue>
 </entry>
 <entry name="use_system_font" mtime="1399646356" type="bool" value="true"/>
 <entry name="title" mtime="1400166548" type="string">
  <stringvalue>h054r7</stringvalue>
 </entry>
 <entry name="bold_color" mtime="1400166548" type="string">
  <stringvalue>#000000000000</stringvalue>
 </entry>
 <entry name="background_type" mtime="1400166548" type="string">
  <stringvalue>transparent</stringvalue>
 </entry>
 <entry name="default_size_columns" mtime="1399646356" type="int" value="80"/>
 <entry name="scrollbar_position" mtime="1400166548" type="string">
  <stringvalue>hidden</stringvalue>
 </entry>
 <entry name="background_darkness" mtime="1400166548" type="float" value="0.95493602752685547"/>
 <entry name="scrollback_unlimited" mtime="1400166548" type="bool" value="true"/>
 <entry name="word_chars" mtime="1399646356" type="string">
  <stringvalue>-A-Za-z0-9,./?%&amp;#:_=+@~</stringvalue>
 </entry>
 <entry name="scrollback_lines" mtime="1400166548" type="int" value="1000"/>
 <entry name="background_color" mtime="1400166548" type="string">
  <stringvalue>#02CF4D7B0000</stringvalue>
 </entry>
 <entry name="foreground_color" mtime="1400166548" type="string">
  <stringvalue>#FFFFFFFFFFFF</stringvalue>
 </entry>
 <entry name="visible_name" mtime="1400166548" type="string">
  <stringvalue>h054r7</stringvalue>
 </entry>
 <entry name="font" mtime="1399646356" type="string">
  <stringvalue>Monospace 12</stringvalue>
 </entry>
 <entry name="cursor_blink_mode" mtime="1399646356" type="string">
  <stringvalue>system</stringvalue>
 </entry>
</gconf>

```

there should be nothing sepcial, just some other colors and the "custom_command". i did never change the "mtime" values, is this maybe the fault?

Edit: here are my 2 scripts, maybe someone wants to do sometime the same thing. but like i said, im not good in scripting
i had to take out some server names :(

cat proxy
```
#################################################################
# Author: Sven Lauber, IT264                                    #
# Date: 04.07.2013                                              #
# Version: 0.1.0                                                #
# Description: Gives everything you need, and a lot more.  #
#################################################################
#!/bin/bash
### Envoirement
PROFILE_CONF="/home/$USER/.go.conf"
GNOME_PROFILE_CONF="/home/$USER/.gconf/apps/gnome-terminal/global/%gconf.xml"
ERROR_OUTPUT="/var/log/proxy/Gprofile_error.log"
SERVICE_NAME=$2
TARGET_HOSTS="
host1 host2
host3 host4
host5 host6
 host7 host8"

USAGE="Usage: proxy [OPTION]... [SERVICE]...
Gives everything you need, and a lot more.
If u use proxy the first time please run -i for initial installation.
After then use the -p option to configure the gnome-terminals for 
the go functionality. 
  -a  shows the port443-access.log from the given service.
  -c  show the httpd.conf file of the given service.
  -e  show the port443-error.log from the given service.
  -g  open gnome-termianls which jumps to the server on where the service is installed.
  -i  create all the needed files to make proxy working.
  -m  modsecurity report (report and rulreport) of the given service.
  -p  create the gnome-terminals profiles for each service. This
  has to run each time when new services got installed on Proxy.
  -t  make a tail on the port443-access.log of the fiven service.
  -z  check the certifiace for the expire date from the given service.
  -y  gives you parameter and information about the given serivce.
  -x  show the change log.
  -?  display this help and exit.
"
### Functions
function get_service {
 # Get the hostname on which the service is running
 HOSTS_TARGET=$( grep "$1" $PROFILE_CONF | cut -f2- -d " " )
 host1=$(echo $HOSTS_TARGET | cut -d " " -f1)
 host2=$(echo $HOSTS_TARGET | cut -d " " -f2)
 # Check if the synthax was right and we got the hosts
 if [ -z "$HOSTS_TARGET" ]; then
  echo "$USAGE"
  exit 1
 fi
}

function set_service {
        for host in $*; do
                services=`ssh hnix1a ssh $host "ls /opt/apache22w/conf/httpd.conf_* | cut -d "_" -f2"`
                for service in $services; do
   echo -e "$service\t$host"
                done
        done | sort | awk -vOFS="\t" 'cs==$1 {hs=hs"\t"$2;next}; {if(cs!=""){print cs,hs}; cs=$1; hs=$2}; END {print cs,hs}' >> $PROFILE_CONF
}

# Function to print red WARRNING messages
function print_red {
 echo -e "\033[31;5;148m\033[1m$*\033[0m"
}

# Function to print green DONE messages
function print_green {
 echo -e "\033[32;5;148m$*\033[0m"
}

# Function to print yellow RUNNING messages
function print_yellow {
 echo -e "\033[33;5;148m\033[1m$*\033[0m"
}
# Function to create the XML file
function create_xml() {
 plattform=$1
 hosts="$2 $3"
 shift
 case $plattform in
 *prod*)
  color="480000000000"
  ;;
 *int*)
  color="60C65F010000"
  ;;
 *test*)
  color="02CF4D7B0000"
  ;;
 *)
  color="480000000000"
  ;;
 esac
 for host in $hosts; do
  mkdir /home/$USER/.gconf/apps/gnome-terminal/profiles/$host  2> $ERROR_OUTPUT
  cp -r /home/$USER/.gconf/apps/gnome-terminal/profiles/TEMPLATE/%gconf.xml /home/$USER/.gconf/apps/gnome-terminal/profiles/$host/%gconf.xml 2> $ERROR_OUTPUT
  sed -i 's/XXXXX/'$host'/g' /home/$USER/.gconf/apps/gnome-terminal/profiles/$host/%gconf.xml
  sed -i 's/YYYYY/'$color'/g' /home/$USER/.gconf/apps/gnome-terminal/profiles/$host/%gconf.xml
 # print_green "Create /home/$USER/.gconf/apps/gnome-terminal/profiles/$host"
 done
}

function existing_file {
 file=$(basename $1)
 if [ "$2" == "p" ]; then
  if [ ! -f $1 ]; then
   sudo cp $file $1 2> $ERROR_OUTPUT
  fi
 else
  if [ ! -f $1 ]; then
   cp $file $1 2> $ERROR_OUTPUT
  fi
 fi
}

# Dont be root because of the permissions and root cant do ssh
if [ "$(whoami)" == "root" ]; then
 print_red "Do not run proxy as root!"
 exit 2
fi
### non-option argument
if [ $# -eq 0 ]; then
 echo -e "$USAGE" >&2
 exit 1
fi
### Parse command line options
while getopts "acegimptyxz?" OPT; do
 case "$OPT" in
  a)
   OPTION="access"
   ;;
  c)
   OPTION="config"
   ;;
  e)
   OPTION="error"
   ;;
  g)
   OPTION="go"
   ;;
  i)
   OPTION="initial"
   ;;
  m)
   OPTION="modsecurity"
   ;;
  p)
   OPTION="profile"
   ;;
  t)
   OPTION="tail"
   ;;
  x)
   OPTION="changelog"
   ;;
  y)
   OPTION="information"
   ;;
  z)
   OPTION="zertifikat"
   ;;
  \?)
   OPTION="help"
   ;;
 esac
done

### Remove the switches we parsed above
shift `expr $OPTIND - 1`

### Print the help
if [ "$OPTION" == "help" ]; then
 echo -e "$USAGE"
 exit 1
fi

### Do the hard work
## ACCESS
if [ "$OPTION" == "access" ]; then
 get_service $SERVICE_NAME
 for HOST in $HOSTS_TARGET; do
  ssh hnix1a ssh $HOST grep -v heartbeat /logs/weblogs/apache/$SERVICE_NAME/port443-access.log | sed "s/^/$HOST: /g"
 done | less -S
fi

## ERROR
if [ "$OPTION" == "error" ]; then
 get_service $SERVICE_NAME
 for HOST in $HOSTS_TARGET; do
  ssh hnix1a ssh $HOST grep -v ModSecurity /logs/weblogs/apache/$SERVICE_NAME/port443-error.log | sed "s/^/$HOST: /g" | sort -u &2>/dev/null
 done | less -S
fi

## GO
if [ "$OPTION" == "go" ]; then
 get_service $SERVICE_NAME
 for HOST in $HOSTS_TARGET; do
  OPTS="$OPTS --tab-with-profile=$HOST"
 done
 gnome-terminal $OPTS
fi

## INITIAL
if [ "$OPTION" == "initial" ]; then
 print_yellow Collect all the needed informations from the remote server
 
 # Clear the available .go.conf
 echo "" > /home/$USER/.go.conf
 # Get the services on each server
 set_service $TARGET_HOSTS
 # Get the customized .go.conf_static
 cat /home/$USER/.go.conf_static >> /home/$USER/.go.conf
fi

## CREATE
if [ "$OPTION" == "profile" ]; then
 print_yellow Create the gnome-terminal profiles
 sudo mkdir /var/log/proxy/ 2> $ERROR_OUTPUT
 sudo chown $USER:$USER /var/log/proxy/ 2> $ERROR_OUTPUT
 touch /var/log/proxy/Gprofile_error.log
 if [ -f $(dirname $GNOME_PROFILE_CONF) ]; then
  mkdir $(dirname $GNOME_PROFILE_CONF)
 fi
 # Envoirement for creating the xml file
        PROFILE_HEADER="<?xml version=\"1.0\"?>\n
        <gconf>\n\t
                <entry name=\"default_profile\" mtime=\"1399646356\" type=\"string\">\n\t\t
                        <stringvalue>Default</stringvalue>\n\t
                </entry>\n\t
                <entry name=\"profile_list\" mtime=\"1399646356\" type=\"list\" ltype=\"string\">\n
        \t\t<li type=\"string\"><stringvalue>Default</stringvalue></li>"
        PROFILE_FOOTER="\t</entry>\n</gconf>"

 # Cleanup - Remove the existing files
        rm -rf /home/$USER/.gconf/apps/gnome-terminal/profiles/h* 2> $ERROR_OUTPUT
        rm -rf /home/$USER/.gconf/apps/gnome-terminal/profiles/v* 2> $ERROR_OUTPUT
 print_green "Remove old gnome-profiles in /home/$USER/.gconf/apps/gnome-terminal/profiles/"
 # Check and copy all the needed files
 existing_file "/home/$USER/.go.conf"
 existing_file "/home/$USER/.go.conf_static"
 
 # ugly hack
 mkdir /home/$USER/.gconf/apps/gnome-terminal/profiles/TEMPLATE 2> $ERROR_OUTPUT
 if [ -f /home/$USER/.gconf/apps/gnome-terminal/profiles/TEMPLATE/%gconf.xml ]; then
  cp ./%gconf.xml /home/$USER/.gconf/apps/gnome-terminal/profiles/TEMPLATE/%gconf.xml 2> $ERROR_OUTPUT
 fi
 existing_file "/home/$USER/.gconf/apps/gnome-terminal/profiles/global/%gconf.xml"
 existing_file "/etc/bash_completion.d/proxy_completion" "p"
 existing_file "/usr/sbin/go" "p"
 existing_file "/usr/bin/go" "p"
 existing_file "/usr/sbin/proxy" "p"
 existing_file "/usr/bin/proxy" "p"
 # Fill in the xml files
 echo -e $PROFILE_HEADER > $GNOME_PROFILE_CONF 2> $ERROR_OUTPUT
 for HOST in $( cut -f2- /home/$USER/.go.conf ); do
  echo -e "\t\t<li type=\"string\"><stringvalue>$HOST</stringvalue></li>"
 done | sort -u >> $GNOME_PROFILE_CONF 2> $ERROR_OUTPUT
 echo -e $PROFILE_FOOTER >> $GNOME_PROFILE_CONF 2> $ERROR_OUTPUT

        #create profiles
        while read profile hosts;
 do
  create_xml $profile $hosts
 done < /home/$USER/.go.conf
        print_red "! You have to logout / login to make the new profiles visible and working !"
fi

# This option has still a bug, and does not what it should do
if [ "$OPTION" == "tail" ]; then
 print_red "This option has still a bug, and does not what it should do"
# get_service $SERVICE_NAME
# ssh hnix1a ssh $host1 tail -f /logs/weblogs/apache/$SERVICE_NAME/port443-access.log >> /tmp/tmp.log &
# echo $1
# ssh hnix1a ssh $host2 tail -f /logs/weblogs/apache/$SERVICE_NAME/port443-access.log >> /tmp/tmp.log &
# echo $2
fi

if [ "$OPTION" == "modsecurity" ]; then
 clear
 get_service $SERVICE_NAME
 print_yellow "ModSecurity-Rulereport"
 ssh hnix1a "7daysaccesslogs.sh -H $host1 $SERVICE_NAME | modsec-positives-rulereport.rb"
 print_yellow "ModSecurity-Report"
 ssh hnix1a "7daysaccesslogs.sh -H $host1 $SERVICE_NAME | modsec-positives-report.rb | grep -v 'Report containing services' | grep -v 'Ports 443'"
fi

if [ "$OPTION" == "zertifikat" ]; then
 clear
 OPENSSL_OUTPUT=$(echo "GET / HTTP/1.0 EOT" | openssl s_client -connect $SERVICE_NAME:443 2>/dev/null);
 CERT_EXPIRE_DATE=$(echo "$OPENSSL_OUTPUT" | sed -n '/-----BEGIN CERTIFICATE-----/,/-----END CERTIFICATE-----/p'| openssl x509 -enddate -noout | cut -d "=" -f2 2>/dev/null);
 print_green "Certifikate information"
 print_yellow "Service:\t$SERVICE_NAME"
 print_yellow "ExpireDate:\t$CERT_EXPIRE_DATE"
fi

if [ "$OPTION" == "information" ]; then
 clear
 get_service $SERVICE_NAME
 print_green "Information about: $SERVICE_NAME"
 print_yellow "Listen adresses:"
 # Loop for each host, and we have at least 2 of theme
 for HOST in $HOSTS_TARGET; do
  LISTEN_HOST=$(ssh hnix1a ssh $HOST grep Listen /opt/apache22w/conf/httpd.conf_$SERVICE_NAME | sed -n 's/:80//gp' | sed -n 's/Listen//gp')
  echo -e "\t$HOST: $LISTEN_HOST";
 done
 # Unique information collection
 LOGIN=$(ssh hnix1a ssh $host1 grep CASLoginURL /opt/apache22w/conf/httpd.conf_$SERVICE_NAME | cut -d "/" -f4);
 REWRITE=$(ssh hnix1a ssh $host1 grep RewriteRule /opt/apache22w/conf/httpd.conf_$SERVICE_NAME | grep -v heartbeat | grep -v favicon | grep -v robots.txt | grep -v errordocuments | grep -v post-sys | grep -v qos | grep -v "#" | sed 's/    RewriteRule/\tRewriteRule/g'); 
 LIMIT=$(ssh hnix1a ssh $host1 grep Limit /opt/apache22w/conf/httpd.conf_$SERVICE_NAME | sed 's/^/\\t/g');
 print_yellow "Login method:"
 echo -e "\t$LOGIN"
 print_yellow "Limit:"
 echo -e "$LIMIT"
 print_yellow "RewriteRules:"
 echo -e "$REWRITE"
fi

if [ "$OPTION" == "config" ]; then
 get_service $SERVICE_NAME
 
 ssh hnix1a ssh $host1 cat /opt/apache22w/conf/httpd.conf_$SERVICE_NAME | less
fi

if [ "$OPTION" == "changelog" ]; then
print_yellow "####### Changelog for proxy
# 0.0.1
# - add "profile" functionality
# - add "initial" functinality
#
# 0.0.2
# - add "go" functionaltiy
#
# 0.0.3
# - add "access" functionaltiy
# - add "error" functionalltiy
#
# 0.0.4
# - add "modsecurity" functionality
#
# 0.0.5
# - add "certificate" functionality
#
# 0.0.6
# - change the help-output
#
# 0.0.7
# - add function which handles the colors "red" "green" "yellow"
#  - bugfix of certificate output, now it shows just what it should
#
# 0.0.8
# - bugfix which did not creat all terminal-profiles.
# - add change log
#
# 0.0.9
# - add function which shows you the config file of the given service
#
# 0.1.0
# - add the information function, which shows you some information about the given service
#
# 0.1.1
# - add a loop for the stuff which does the "information" things
#
# 0.1.2
# - add "tail" functionality. or at least first darft of it
"
fi

```


cat proxy_completion
```
_proxy() 
{
 OPTIONS=$(cut -f1 /home/$USER/.go.conf)
    
 local cur prev opts
 COMPREPLY=()
 cur="${COMP_WORDS[COMP_CWORD]}"
 prev="${COMP_WORDS[COMP_CWORD-1]}"
 opts="$OPTIONS"
 if [[ ${cur} == -* ]] ; then
  COMPREPLY=($(compgen -W "${opts}" -- ${cur}))
  return 0
 fi
 COMPREPLY=($( grep "^${cur//./\\.}" /home/$USER/.go.conf | cut -f1 ))
}
complete -F _proxy proxy
```

and the config file looks like this after it is generated

example:

cat .go.conf
```

[www.url1.com]("http://www.url1.com")   host1 host2
[www.url2.com]("http://www.url2.com")   host3 host4

```

---


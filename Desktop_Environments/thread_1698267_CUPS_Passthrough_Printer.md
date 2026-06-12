---
title: "CUPS Passthrough Printer?"
date: 2011-03-02
forum: Desktop Environments
---

### Post by mwray on 2011-03-02
Is it possible to setup a "printer" that really takes a printjob and passes it to a process which will forward to another printer?

Here is the scenario: Brother does not make a "Print to Fax" driver, although it handles faxes as print jobs. I cannot just "Print" to the BRFAX printer though. I must currently first save my file as a PS or a PDF, then call brpcfax -P BRFAX -o PAPER=LETTER  $filename.

This will then fax the appropriate file.


I would like to create a printer that automates this process. Is this possible? If so, what's the easiest way.:)

---

### Post by mwray on 2011-03-02
Here's what I've tried so far.

Create /var/spool/brp2fax owned by root:lp w 555 privileges. Enabled FileDevice in /etc/cups/cupsd.conf

Setting up BRFAX per instructions on forums (For brother printers). Creating a script (ala lpadmin type script) then issueing:
sudo lpadmin -P PRINT2FAX -v /var/spool/br2fax/  -i brp2f

This creates a printer, but complains about copying the script saying it doesn't exist. (I've even tried giving full path to the new script after the -i command) 

Any suggestions? The printer gets created and "finishes" jobs,  but brpcfax is not popping up.
(Called as bcpcfax -P BRFAX -o PAPER=LETTER $file  from in the script)
Jobs are spooled, and "processed" but not being passed to brpcfax.
script is as follows:
```

#/bin/sh
#
#       Copyright (c) 1997, by Sun Microsystems Inc.
#       All Rights Reserved
#
#pragma ident   "@(#)interface.html     1.2     98/05/22 SM"
#
#       This is an example interface script to help you get an idea of how
# to integrate support for your printer under lp.  This is by no means the
# definitive source for information.  You should look at included interface
# scripts as examples and at the Solaris System Administrators Answerbook.
#
# This script is run as 'lp' on the print server if the job came in via the
# network.  It runs as the submitting user if the job is local.  You should
# also note that the data files are owned by the user running the script.
#
# Command Line Arguments:
#       $0      - .../{printer}
#       $1      - request-id
#       $2      - user
#       $3      - title
#       $4      - copies
#       $5      - options (lp -o)
#       $6+     - file list
# Environment Variables:
#       CHARSET         - the character set to use
#       FILTER          - fast filter to inline on the way to the printer
#       LC_COLLATE      - I18n
#       LC_CTYPE        - I18n
#       LC_MESSAGES     - I18n
#       LC_MONETARY     - I18n
#       LC_NUMERIC      - I18n
#       LC_TIME         - I18n
#       PATH            - default path (/usr/sbin:/usr/bin)
#       SPOOLER_KEY     - used by lp.tell for backchannel to lpsched
#       TERM            - printer type
#       TZ              - our timezone
# File Descriptors:
#       0       - don't recall
#       1       - printer device (use /dev/null for network attached
# printers)
#       2       - backchannel to lpsched
# Signals:
#
# Exit Codes:
#       0       - success
#       1 - 127 - failure, don't restart
#       128     - don't use
#       >128    - failure, wait or restart
#

if [ $# -lt 5 ] ; then
        echo "wrong number of arguments to interface program" 1>&2
        exit 1
fi


printer=`basename $0`
request_id=$1
user_name=$2
title=$3
copies=$4
option_list=$5

shift 5
files="$*"

stty=

parse () {
        echo "`expr \"$1\" : \"^[^=]*=\(.*\)\"`"
}

nobanner="no"
nofilebreak="no"
inlist=
for i in ${option_list}
do
        case "${inlist}${i}" in

        nobanner )
                nobanner="yes"
                ;;

        nofilebreak )
                nofilebreak="yes"
                ;;

# lp -o key
#       key )
#               key="whatever"
#               ;;

# lp -o key=value
#       key=* )
#               key=`parse ${i}`
#               ;;

# lp -o key='list ...'
#       stty=* )
#               inlist=`expr "${inlist}${i}" : "^\([^=]*=\)"`
#               case "${i}" in
#               ${inlist}\'*\' )
#                       item=`expr "${i}" : "^[^=]*='*\(.*\)'\$"`
#                       ;;
#               ${inlist}\' )
#                       continue
#                       ;;
#               ${inlist}\'* )
#                       item=`expr "${i}" : "^[^=]*='*\(.*\)\$"`
#                       ;;
#               ${inlist}* )
#                       item=`expr "${i}" : "^[^=]*=\(.*\)\$"`
#                       ;;
#               *\' )
#                       item=`expr "${i}" : "^\(.*\)'\$"`
#                       ;;
#               * )
#                       item="${i}"
#                       ;;
#               esac
#
#               #####
#               #
#               # We don't dare use "eval" because a clever user could
#               # put something in an option value that we'd end up
#               # exec'ing.
#               #####
#               case "${inlist}" in
#               key= )
#                       key="${key} ${item}"
#                       ;;
#               esac
#
#               case "${i}" in
#               ${inlist}\'*\' )
#                       inlist=
#                       ;;
#               ${inlist}\'* )
#                       ;;
#               *\' | ${inlist}* )
#                       inlist=
#                       ;;
#               esac
#               ;;
        * )
                echo "unrecognized \"-o ${i}\" option check the option,
resubmit if necessary printing continues" 1>&2
                ;;
        esac
done

#
# should create a banner
#

#
# process the files
#

i=1
while [ $i -le $copies ]
do
        for file in $files
        do
                brpc2fax -P BRFAX -o Paper=Letter $file
        done
        i=`expr $i + 1`
done


```

---


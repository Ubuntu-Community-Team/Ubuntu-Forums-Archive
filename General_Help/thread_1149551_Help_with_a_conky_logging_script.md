---
title: "Help with a conky logging script"
date: 2009-05-05
forum: General Help
---

### Post by Akovia on 2009-05-05
Hi,
I was hoping someone could help me figure out what I'm doing wrong here. I downloaded a logging script for conky that was written for sh. When I run it, it seems that it's not interpreted at all so I wasn't sure if it could be fixed to run on bash or if there was something else I'm missing.

I must admit I don't fully understand what the differences are between the two, so I might be completely off track trying to do this at all.

Here is the script itself.  

> #!/bin/sh
2     
3     #
4     VERSION="0.2"
5     # $Id$
6     #
7     
8     
9     
10     #
11     # DESCRIPTION
12     #
13     #   Formats `tail /var/log/messages` to suit conky's layout - at least my own.
14     #   /var/log/messages might be root rw------- on your system, so you'll have to
15     #+  add some configuration directive.
16     #   Using syslog-ng, add this line to /etc/syslog-ng/syslog-ng.conf:
17     #       options { group(1000) ; perm(0640); };
18     #   (make sure to use *your* gid). Then restart syslog-ng:
19     #       /etc/init.d/syslog-ng restart
20     #
21     
22     
23     
24     #
25     # CHANGELOG
26     #
27     #   0.1
28     #   - Script creation
29     #   0.2
30     #   - Added --fold --lines --version --help
31     #
32     
33     
34     
35     #
36     # CONFIGURATION
37     #
38     
39     # File to tail
40     MESSAGES=/var/log/messages
41     
42     # Max lines to parse before displaying
43     PARSELINES=60
44     # Default max lines to show in conky
45     DEFAULTDISPLAYLINES=8
46     
47     # Default fold to X characters
48     DEFAULTFOLD=68
49     
50     # Exit codes
51     E_USAGE=64
52     E_BADARGS=65
53     E_NOPERM=77
54     E_NOSUCHFILE=66
55     
56     
57     
58     #
59     # FUNCTIONS
60     #
61     
62     print_usage() {
63         echo "$0 v${VERSION} - Filters tail ${MESSAGES}.
64     
65     $0 is a script that parses $MESSAGES}, filtering out the crap.
66     
67     Usage: $0 [OPTION...]
68     
69     Options:
70       -f, --fold        use N columns instead of ${DEFAULTFOLD}.
71       -n, --lines       Output the last N lines, instead of the last ${DEFAULTDISPLAYLINES}.
72     
73     Other options:
74       -h, --help        This help message.
75       -v, --version     Output version information and exit.
76     "
77     }
78     
79     
80     
81     #
82     # Errors handling
83     #
84     
85     if [ ! -e $MESSAGES ] ; then
86         echo "ERROR: can not read $MESSAGES (no such file)" 1>&2
87         exit $e_NOSUCHFILE
88     fi
89     
90     if [ ! -r $MESSAGES ] ; then
91         echo "ERROR: can not read $MESSAGES (permission denied)" 1>&2
92         exit $E_NOPERM
93     fi
94     
95     
96     
97     #
98     # ARGS
99     #
100     
101     if [ $# -ne 0 ] ; then
102         while test $# -gt 0; do
103             case $1 in
104                 -h|--help)
105                     print_usage
106                     exit 0 ;;
107                 -v|--version)
108                     echo "$0 $VERSION"
109                     exit 0 ;;
110                 -f|--fold)
111                     shift
112                     # TODO: Needs to test if $1 is an integer
113                     FOLD=$1
114                     shift
115                     continue
116                     ;;
117                 -n|--lines)
118                     shift
119                     # TODO: Needs to test if $1 is an integer
120                     DISPLAYLINES=$1
121                     shift
122                     continue
123                     ;;
124                 *)
125                     echo "ERROR: unknown option: $1" >&2
126                     exit $E_USAGE ;;
127             esac
128         done
129     fi
130     
131     [ -z $DISPLAYLINES ] && DISPLAYLINES=${DEFAULTDISPLAYLINES}
132     [ -z $FOLD ]         && FOLD=${DEFAULTFOLD}
133     
134     
135     
136     #
137     # Read, filter and tail
138     #
139     
140     #  We take a bunch of lines from /var/log/messages
141     #  For each line, we squeeze double spaces ; this for days 1 to 9 of each
142     #+ month, where the double space between the month's name and the day's number
143     #+ would break the cut command below.
144     
145     tail -n $PARSELINES $MESSAGES | tr -s " "                   | \
146         while read line ; do
147     
148             # For each line you don't want to see, add a continue case statement
149             case "$(echo $line | cut -d ' ' -f 6-)" in
150                 "(root) CMD (rm -f /var/spool/cron/lastrun/cron.hourly)")
151                     continue
152                     ;;
153                 "(root) CMD (rm -f /var/spool/cron/lastrun/cron.daily)")
154                     continue
155                     ;;
156                 "(root) CMD (rm -f /var/spool/cron/lastrun/cron.weekly)")
157                     continue
158                     ;;
159                 "(root) CMD (rm -f /var/spool/cron/lastrun/cron.monthly)")
160                     continue
161                     ;;
162                 "(root) CMD (test -x /usr/sbin/run-crons && /usr/sbin/run-crons )")
163                     continue
164                     ;;
165                 *)
166                     echo "$line"
167                     ;;
168             esac
169         #  Once this filtering is done, format the output to fit to conky's layout.
170         #  cut: we don't need the day, we don't need the host.
171         #  fold: fold to 68 characters or it will break the conky's window width.
172         #  tail: finaly keep only the 8 last lines.
173         done | \
174         cut -d ' ' -f 3,5-          | \
175         fold -s -w $FOLD            | \
176         tail -n $DISPLAYLINES
177     
178     
179     
180     # Exits sucessfully
181     exit 0Called by this in conky

> ${color3}${exec ~/.conky/my_scripts/tail-varlogmessages.sh --fold 68 --lines 8}And here is the output.

> /home/progex/.conky/my_scripts/tail-varlogmessages.sh: 2: 2: not found
/home/progex/.conky/my_scripts/tail-varlogmessages.sh: 3: 3: not found
/home/progex/.conky/my_scripts/tail-varlogmessages.sh: 4: 4: not found
/home/progex/.conky/my_scripts/tail-varlogmessages.sh: 5: 5: not found
/home/progex/.conky/my_scripts/tail-varlogmessages.sh: 6: 6: not found
/home/progex/.conky/my_scripts/tail-varlogmessages.sh: 7: 7: not found
/home/progex/.conky/my_scripts/tail-varlogmessages.sh: 8: 8: not found
/home/progex/.conky/my_scripts/tail-varlogmessages.sh: 9: 9: not found
/home/progex/.conky/my_scripts/tail-varlogmessages.sh: 10: 10: not found
/home/progex/.conky/my_scripts/tail-varlogmessages.sh: 11: 11: not found
/home/progex/.conky/my_scripts/tail-varlogmessages.sh: 12: 12: not found
/home/progex/.conky/my_scripts/tail-varlogmessages.sh: 13: 13: not found
/home/progex/.conky/my_scripts/tail-varlogmessages.sh: 14: 14: not found
/home/progex/.conky/my_scripts/tail-varlogmessages.sh: 15: 15: not found
/home/progex/.conky/my_scripts/tail-varlogmessages.sh: 16: 16: not found
/home/progex/.conky/my_scripts/tail-varlogmessages.sh: 17: 17: not found
/home/progex/.conky/my_scripts/tail-varlogmessages.sh: 18: 18: not found
/home/progex/.conky/my_scripts/tail-varlogmessages.sh: 19: 19: not found
/home/progex/.conky/my_scripts/tail-varlogmessages.sh: 20: 20: not found
/home/progex/.conky/my_scripts/tail-varlogmessages.sh: 21: 21: not found
/home/progex/.conky/my_scripts/tail-varlogmessages.sh: 22: 22: not found
/home/progex/.conky/my_scripts/tail-varlogmessages.sh: 23: 23: not found
/home/progex/.conky/my_scripts/tail-varlogmessages.sh: 24: 24: not found
/home/progex/.conky/my_scripts/tail-varlogmessages.sh: 25: 25: not found
/home/progex/.conky/my_scripts/tail-varlogmessages.sh: 26: 26: not found
/home/progex/.conky/my_scripts/tail-varlogmessages.sh: 27: 27: not found
/home/progex/.conky/my_scripts/tail-varlogmessages.sh: 28: 28: not found
/home/progex/.conky/my_scripts/tail-varlogmessages.sh: 29: 29: not found
/home/progex/.conky/my_scripts/tail-varlogmessages.sh: 30: 30: not found
/home/progex/.conky/my_scripts/tail-varlogmessages.sh: 31: 31: not found
/home/progex/.conky/my_scripts/tail-varlogmessages.sh: 32: 32: not found
/home/progex/.conky/my_scripts/tail-varlogmessages.sh: 33: 33: not found
/home/progex/.conky/my_scripts/tail-varlogmessages.sh: 34: 34: not found
/home/progex/.conky/my_scripts/tail-varlogmessages.sh: 35: 35: not found
/home/progex/.conky/my_scripts/tail-varlogmessages.sh: 36: 36: not found
/home/progex/.conky/my_scripts/tail-varlogmessages.sh: 37: 37: not found
/home/progex/.conky/my_scripts/tail-varlogmessages.sh: 38: 38: not found
/home/progex/.conky/my_scripts/tail-varlogmessages.sh: 39: 39: not found
/home/progex/.conky/my_scripts/tail-varlogmessages.sh: 40: 40: not found
/home/progex/.conky/my_scripts/tail-varlogmessages.sh: 41: 41: not found
/home/progex/.conky/my_scripts/tail-varlogmessages.sh: 42: 42: not found
/home/progex/.conky/my_scripts/tail-varlogmessages.sh: 43: 43: not found
/home/progex/.conky/my_scripts/tail-varlogmessages.sh: 44: 44: not found
/home/progex/.conky/my_scripts/tail-varlogmessages.sh: 45: 45: not found
/home/progex/.conky/my_scripts/tail-varlogmessages.sh: 46: 46: not found
/home/progex/.conky/my_scripts/tail-varlogmessages.sh: 47: 47: not found
/home/progex/.conky/my_scripts/tail-varlogmessages.sh: 48: 48: not found
/home/progex/.conky/my_scripts/tail-varlogmessages.sh: 49: 49: not found
/home/progex/.conky/my_scripts/tail-varlogmessages.sh: 50: 50: not found
/home/progex/.conky/my_scripts/tail-varlogmessages.sh: 51: 51: not found
/home/progex/.conky/my_scripts/tail-varlogmessages.sh: 52: 52: not found
/home/progex/.conky/my_scripts/tail-varlogmessages.sh: 53: 53: not found
/home/progex/.conky/my_scripts/tail-varlogmessages.sh: 54: 54: not found
/home/progex/.conky/my_scripts/tail-varlogmessages.sh: 55: 55: not found
/home/progex/.conky/my_scripts/tail-varlogmessages.sh: 56: 56: not found
/home/progex/.conky/my_scripts/tail-varlogmessages.sh: 57: 57: not found
/home/progex/.conky/my_scripts/tail-varlogmessages.sh: 58: 58: not found
/home/progex/.conky/my_scripts/tail-varlogmessages.sh: 59: 59: not found
/home/progex/.conky/my_scripts/tail-varlogmessages.sh: 60: 60: not found
/home/progex/.conky/my_scripts/tail-varlogmessages.sh: 61: 61: not found
/home/progex/.conky/my_scripts/tail-varlogmessages.sh: 62: Syntax error: "(" unexpectedIs there anything I can do to get this to work?

Many Thanks,
Akovia

---

### Post by hexanol on 2009-05-05
Well, each lines (except the first one) start with a number. Start by removing these numbers. Right now you are getting problems because of this.

---

### Post by Akovia on 2009-05-05
*sigh* I figured it out. Please feel free to delete this.

I don't know why the numbering was included in the script but it works once they were removed.

For anyone that wants the script, here's the fixed version.

> #!/bin/sh
     
     #
     VERSION="0.2"
     # $Id$
     #
     
     
     
     #
     # DESCRIPTION
     #
     #   Formats `tail /var/log/messages` to suit conky's layout - at least my own.
     #   /var/log/messages might be root rw------- on your system, so you'll have to
     #+  add some configuration directive.
     #   Using syslog-ng, add this line to /etc/syslog-ng/syslog-ng.conf:
     #       options { group(1000) ; perm(0640); };
     #   (make sure to use *your* gid). Then restart syslog-ng:
     #       /etc/init.d/syslog-ng restart
     #
     
     
     
     #
     # CHANGELOG
     #
     #   0.1
     #   - Script creation
     #   0.2
     #   - Added --fold --lines --version --help
     #
     
     
     
     #
     # CONFIGURATION
     #
     
     # File to tail
     MESSAGES=/var/log/messages
     
     # Max lines to parse before displaying
     PARSELINES=60
     # Default max lines to show in conky
     DEFAULTDISPLAYLINES=8
     
     # Default fold to X characters
     DEFAULTFOLD=68
     
     # Exit codes
     E_USAGE=64
     E_BADARGS=65
     E_NOPERM=77
     E_NOSUCHFILE=66
     
     
     
     #
     # FUNCTIONS
     #
     
     print_usage() {
         echo "$0 v${VERSION} - Filters tail ${MESSAGES}.
     
     $0 is a script that parses $MESSAGES}, filtering out the crap.
     
     Usage: $0 [OPTION...]
     
     Options:
       -f, --fold        use N columns instead of ${DEFAULTFOLD}.
       -n, --lines       Output the last N lines, instead of the last ${DEFAULTDISPLAYLINES}.
     
     Other options:
       -h, --help        This help message.
       -v, --version     Output version information and exit.
     "
     }
     
     
     
     #
     # Errors handling
     #
     
     if [ ! -e $MESSAGES ] ; then
         echo "ERROR: can not read $MESSAGES (no such file)" 1>&2
         exit $e_NOSUCHFILE
     fi
     
     if [ ! -r $MESSAGES ] ; then
         echo "ERROR: can not read $MESSAGES (permission denied)" 1>&2
         exit $E_NOPERM
     fi
     
     
     
     #
     # ARGS
     #
     
     if [ $# -ne 0 ] ; then
         while test $# -gt 0; do
             case $1 in
                 -h|--help)
                     print_usage
                     exit 0 ;;
                 -v|--version)
                     echo "$0 $VERSION"
                     exit 0 ;;
                 -f|--fold)
                     shift
                     # TODO: Needs to test if $1 is an integer
                     FOLD=$1
                     shift
                     continue
                     ;;
                 -n|--lines)
                     shift
                     # TODO: Needs to test if $1 is an integer
                     DISPLAYLINES=$1
                     shift
                     continue
                     ;;
                 *)
                     echo "ERROR: unknown option: $1" >&2
                     exit $E_USAGE ;;
             esac
         done
     fi
     
     [ -z $DISPLAYLINES ] && DISPLAYLINES=${DEFAULTDISPLAYLINES}
     [ -z $FOLD ]         && FOLD=${DEFAULTFOLD}
     
     
     
     #
     # Read, filter and tail
     #
     
     #  We take a bunch of lines from /var/log/messages
     #  For each line, we squeeze double spaces ; this for days 1 to 9 of each
     #+ month, where the double space between the month's name and the day's number
     #+ would break the cut command below.
     
     tail -n $PARSELINES $MESSAGES | tr -s " "                   | \
         while read line ; do
     
             # For each line you don't want to see, add a continue case statement
             case "$(echo $line | cut -d ' ' -f 6-)" in
                 "(root) CMD (rm -f /var/spool/cron/lastrun/cron.hourly)")
                     continue
                     ;;
                 "(root) CMD (rm -f /var/spool/cron/lastrun/cron.daily)")
                     continue
                     ;;
                 "(root) CMD (rm -f /var/spool/cron/lastrun/cron.weekly)")
                     continue
                     ;;
                 "(root) CMD (rm -f /var/spool/cron/lastrun/cron.monthly)")
                     continue
                     ;;
                 "(root) CMD (test -x /usr/sbin/run-crons && /usr/sbin/run-crons )")
                     continue
                     ;;
                 *)
                     echo "$line"
                     ;;
             esac
         #  Once this filtering is done, format the output to fit to conky's layout.
         #  cut: we don't need the day, we don't need the host.
         #  fold: fold to 68 characters or it will break the conky's window width.
         #  tail: finaly keep only the 8 last lines.
         done | \
         cut -d ' ' -f 3,5-          | \
         fold -s -w $FOLD            | \
         tail -n $DISPLAYLINES
     
     
     
     # Exits sucessfully
     exit 0Ako

---


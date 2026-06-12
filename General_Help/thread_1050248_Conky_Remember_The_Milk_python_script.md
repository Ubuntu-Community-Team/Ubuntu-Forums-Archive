---
title: "Conky Remember The Milk python script"
date: 2009-01-25
forum: General Help
---

### Post by TheAxeR on 2009-01-25
I just finished writing a python3 script for conky to display my remember the milk task due on a particular day.  

The general usage is
```

$ python3 conkyRTM.py username password day_you_want_listed 

```

where day_you_want_listed can be input as today, tomorrow, or an integer which represents a timedelta from today, for example
 0 = today
 1 = tomorrow
 2 = 2 days from today
30 = 30 days from today

This means that the command
```

$ python3 conkyRTM.py username password today

```

and

```

$ python3 conkyRTM.py username password 0

```

Will both output today's due task.

Any task which does not have a due date or the date is set as never will be displayed with today's tasks.  There are two reasons for this.  First it was easier to code this way.  The other reason is that, at least with how I use my todo list, a task which is never due is meant to be a constant reminder.

This script does not take advantage of RTM api, it uses your all task rss feed.

The output looks like
```

Task Due on (date):
     Task 1
     Task 2 

```

This may or may not be the most elegant solution for this, I have just started.  Any suggestions are welcome.  Here is the code:

```

#!/usr/bin/python3
#
# ======================================================================
# Copyright (C) 2009 Lucas David-Roesler <roesler.lucas@gmail.com>
# Time-stamp: Tue January 20, 2009
# This program is free software; you can redistribute it and/or modify
# it under the terms of the GNU General Public License version 2 as
# published by the Free Software Foundation.
# ======================================================================
#
# This script accesses takes in the username, password, and a date then
# retrieves # and outputs the tasks due on that date from the users account at 
# http://www.rememberthemilk.com . The date can be input as Today, Tomorrow, or
# as an integer: 0 = Today, 1 = Tomorrow, 2 = Today + 2 days, etc.  
#
# This is intended to be used with conky: http://conky.sourceforge.net/ .
#
# Note that the username and password are not encrypted or obfruscated in any way.
#
# Currently any task that has a due date of never or an empty due date is
# treated as due today. The thought is that those tasks are meant to be constant
# reminders and therefore always displayed. In the future this may be given an
# option. 

import sys
import urllib.request
from datetime import datetime, date, time, timedelta
from xml.dom.minidom import parse, parseString

RTM = 'https://www.rememberthemilk.com/atom/'

uname = sys.argv[1]
password = sys.argv[2]
list_date = sys.argv[3]


def get_feed():
    '''The method to do HTTPBasicAuthentication'''
    
    link = RTM + uname
    
    # Create an OpenerDirector with support for Basic HTTP Authentication...
    auth_handler = urllib.request.HTTPBasicAuthHandler()
    auth_handler.add_password(realm= 'RememberTheMilk Atom Feed',
                              uri= 'https://www.rememberthemilk.com/',
                              user= uname,
                              passwd= password)
    opener = urllib.request.build_opener(auth_handler)
    # ...and install it globally so it can be used with urlopen.
    urllib.request.install_opener(opener)
    response = urllib.request.urlopen(link)
    feed = response.read() 
    response.close()
    return feed

def getText(node):
    rc = ""
    for child in node.childNodes:
        if child.nodeType == child.TEXT_NODE:
            rc = rc + child.data
    return rc
    
def task_info(parsed,i):
    
    
    tasklist = parsed.getElementsByTagName('entry')
    
    task = tasklist[i]
    
    # get task title
    task_title = task.getElementsByTagName('title')
    title = getText(task_title[0])
    
    # get task contents
    contents_list = task.getElementsByTagName('content')
    task_contents = contents_list[0].getElementsByTagName('span')
    for span in task_contents:
        class_name = span.attributes['class']
        if class_name.value == 'rtm_due_value':
            date_raw = getText(span)
            try:
                date_parsed = datetime.strptime(date_raw, "%a %d %b %y")
            except ValueError:
                try:
                    date_parsed = datetime.strptime(date_raw, "%a %d %b %y at %I:%M%p")
                except ValueError:
                    date_parsed = datetime.today()
            task_due = date_parsed.date()
        if class_name.value == 'rtm_priority_value':
            task_priority = getText(span)
        if class_name.value == 'rtm_time_estimate_value':
            task_time = getText(span)
        if class_name.value == 'rtm_tags_value':
            task_tags = getText(span)
        if class_name.value == 'rtm_location_value':
            task_location = getText(span)
        if class_name.value == 'rtm_postponed_value':
            task_postponed = getText(span)
    
    # create dictionary with task info       
    task_info = {}
    task_info['title'] = title
    task_info['due'] = task_due
    task_info['priority'] = task_priority
    task_info['time'] = task_time
    task_info['tags'] = task_tags
    task_info['location'] = task_location
    task_info['postponed'] = task_postponed
    
    return task_info
     
def convert_date(time):
    
    one_day = timedelta(days=1)
    today = date.today()
    tomorrow = today + one_day

    if time == 'today':
        day = today
    elif time == 'tomorrow':
        day = tomorrow
    else:
        day = today + (int(time) * one_day)
    return day
    
def get_tasks(feed, time):
    
    dom = parseString(feed)
    
    num_task = len(dom.getElementsByTagName('entry'))
    
    task_for_time = []
    
    # Run through all the task and grab the ones 
    # that match the desired due date.
    
    for m in range(0,num_task):
        
        task = task_info(dom,m) 
        
        # I used this line for testing
        # print(task['title'] + ' ' + str(task['due']) + ' ' + str(time))
        
        if str(task['due']) == str(time):
            task_for_time.append(task)
            
    return task_for_time
    
    
if __name__ == "__main__":
    
    # Do auth and then get the feed, strip out garbage at the beginning and the 
    # end of the feed.
    taskfeed = get_feed()[6:-8]

    
    emptylist = []
    
    list_date = convert_date(list_date.lower())       
    
    if list_date == date.today():
        time_title = 'Today'
    elif list_date == date.today()+timedelta(days=1):
        time_title = 'Tomorrow'
    else:
        time_title = 'on ' + list_date.strftime('%a %Y-%m-%d')
    
    # Parse the feed and get grab the tasks with the desired due date.
    # Returns a list of tasks, the tasks are dictionary objects which contains
    # the task information.
    tasklist = get_tasks(taskfeed, list_date) 
    
    print('Tasks Due ' + time_title + ':')
    for task in tasklist:
        print('    '+task['title'])
    if tasklist == emptylist:
        print('    Nothing Due')

```

---

### Post by MusicMastaMike on 2009-02-04
Awesome!  I was looking for this.  I updated your script to accept a comma separated list of days, rather than just 1 day at a time, for instance:
```
./conkyRTM.py username password 0,1,2
```

I'd be happy to contribute to this if you have other ideas!

---

### Post by TheAxeR on 2009-02-04
I am glad someone else found it useful.

I have made a few changes to it as well.  I will not have time to look at what you have done until Friday, but, I added the ability to filter which task lists are displayed.  

With my version it accepts options for a blacklist (task lists you do not want displayed) and a whitelist (task lists you do want to display).  I also pulled out the coding for the color and made the title color and the list color accessible as well.  See below:

```

Usage: conkyRTM.py [options] uname pass list_date 

Options:
-h, --help    show this help message and exit
-w WHITELIST, --whitelist=WHITELIST
            Display only the tasks from specific lists.
            This option requires a separate instance for each list
            you want displayed. i.e. if you want to display only 
            your inbox and your personal list use:
            conkyRTM.py -w Inbox -w Personal uname pass list_date
-b BLACKLIST, --blacklist=BLACKLIST
            Exclude tasks from particular lists.
            This option works the same way as the whitelist:
            conkyRTM.py -b Inbox -b Personal uname pass list_date
            would display all tasks  EXCEPT those from your Inbox 
            or your Personal list.
-t TITLECOLOR, --titlecolor=TITLECOLOR
            For use with Conky.  Specify the color for the title.
-l LISTCOLOR, --listcolor=LISTCOLOR
            For use with Conky.  Specify the color for the list.

```

---

### Post by cdiaz on 2009-02-08
When I run the command  python3 conkyRTM.py myusername mypasswd 1

I get the following error:

Traceback (most recent call last):
  File "conkyRTM.py", line 171, in <module>
    tasklist = get_tasks(taskfeed, list_date) 
  File "conkyRTM.py", line 128, in get_tasks
    dom = parseString(feed)
  File "/usr/lib/python3.0/xml/dom/minidom.py", line 1927, in parseString
    return expatbuilder.parseString(string)
  File "/usr/lib/python3.0/xml/dom/expatbuilder.py", line 940, in parseString
    return builder.parseString(string)
  File "/usr/lib/python3.0/xml/dom/expatbuilder.py", line 223, in parseString
    parser.Parse(string, True)
xml.parsers.expat.ExpatError: not well-formed (invalid token): line 1, column 0

I am a total python noob, so I have no clue what this means.  Any help is appreciated.

---

### Post by TheAxeR on 2009-02-09
Ok, first make sure that you have python 3 installed. The default that comes installed is 2.5.  This can be installed through synaptic.  

Second, if that is not the issue, then please run this script:

```

import sys
import urllib.request
from xml.dom.minidom import parse, parseString

RTM = 'https://www.rememberthemilk.com/atom/'

#required arguments
uname = sys.argv[1]
password = sys.argv[2]



link = RTM + uname

# Create an OpenerDirector with support for Basic HTTP Authentication...
auth_handler = urllib.request.HTTPBasicAuthHandler()
auth_handler.add_password(realm= 'RememberTheMilk Atom Feed',
                        uri= 'https://www.rememberthemilk.com/',
                        user= uname,
                        passwd= password)
opener = urllib.request.build_opener(auth_handler)
# ...and install it globally so it can be used with urlopen.
urllib.request.install_opener(opener)
response = urllib.request.urlopen(link)
feed = response.read() 
response.close()
print(str(feed[:20])+ '   '+str(feed[-20:]))
print('\n')
print(str(feed[6:20])+'   '+str(feed[-20:-8]))

```

It will print out the beginning and end of the feed that it is downloading and the same feed minus the first 6 characters and minus the last 8 characters.  

The output is something like this:
> 
b'436d\r\n<?xml version='   b'ntry></feed>\n\r\n0\r\n\r\n'


b'<?xml version='   b'ntry></feed>'


I ran into this issue when I wrote the script.  For some reason there are some garbage characters at the beginning and the end of the rss feed.  This produces an error in which the parser will complain that the feed is malformed.  My fix was to remove the misbehaving characters from the feed before passing it to the parser.  However, it seems to not have worked in this situation.

There must be a better way of handling the extra characters but I am not sure what the best approach is. 

If you can give me the output of that script then we can verify if this is the issue. 

And do not worry about being a noob, I am certain that I probably know little more then you do about python.

---

### Post by cdiaz on 2009-02-10
When I run the second script I get this output:

b'8ba\r\n<?xml version="'   b'ntry></feed>\n\r\n0\r\n\r\n'


b'?xml version="'   b'ntry></feed>'


Thanks for the quick reply and the help.

Cesar

---

### Post by TheAxeR on 2009-02-10
So it seems that the extra characters in your rss feed are a different length then those in my rss feed.

look in the script for 
```

    # Do auth and then get the feed, strip out garbage at the beginning and the 
    # end of the feed.
    taskfeed = get_feed()[6:-8]


```

To get it to work for your feed you need to change the 6 to a 5, I think.  This should remove the 
> 
8ba\r\n

from the beginning of your feed and it should then parse correctly.  I do not believe that you need to adjust the -8, it is correct in this situation.

---

### Post by cdiaz on 2009-02-10
That worked.  Thanks.

---

### Post by wynneth on 2009-02-19
Ok so I was trying to combine the new version with the fancy options with the one MusicMastaMike posted for multiple days. Apparently I can't. I did manage to insert extra options into it for alignment in addition to list color, so somehow I'm smart enough to do that. Also, I know NOTHING about python. Would someone show me how to properly combine these? Here's mine with the extra arguments that works:
```

#!/usr/bin/python3
#
#revisions:
#
# 30/01/2009:
#    use optparse to parse options, add blacklist/whitelist option, 
#    i.e. show all but your 'Foo' list or only show your 'Foo' list.
#    
#
# ======================================================================
# Copyright (C) 2009 Lucas David-Roesler <roesler.lucas@gmail.com>
# Time-stamp: Tue January 20, 2009
# This program is free software; you can redistribute it and/or modify
# it under the terms of the GNU General Public License version 2 as
# published by the Free Software Foundation.
# ======================================================================
#
# This script accesses takes in the username, password, and a date then
# retrieves # and outputs the tasks due on that date from the users account at 
# http://www.rememberthemilk.com . The date can be input as Today, Tomorrow, or
# as an integer: 0 = Today, 1 = Tomorrow, 2 = Today + 2 days, etc.  
#
# This is intended to be used with conky: http://conky.sourceforge.net/ .
#
# Note that the username and password are not encrypted or obfruscated in any way.
#
# Currently any task that has a due date of never or an empty due date is
# treated as due today. The thought is that those tasks are meant to be constant
# reminders and therefore always displayed. In the future this may be given an
# option. 

import sys
import urllib.request
from optparse import OptionParser
from datetime import datetime, date, time, timedelta
from xml.dom.minidom import parse, parseString

RTM = 'https://www.rememberthemilk.com/atom/'
#whitelist = []
#blacklist = []
#titlecolor = ''
#listcolor = ''
#titlealign = ''
#listalign = ''


# options
usage = "usage: %prog [options] uname pass list_date "
parser = OptionParser(usage)
parser.set_defaults(whitelist=[],blacklist=[],titlecolor='',listcolor='',titlealign='',listalign='')
parser.add_option("-w","--whitelist", action="append",type='string',dest="whitelist",
                  help='Display only the tasks from specific lists. This option requires a separate instance for each list you want displayed. i.e. if you want to display only your inbox and your personal list use: \
                  conkyRTM.py -w Inbox -w Personal uname pass list_date')

parser.add_option("-b","--blacklist", action="append",type='string',dest="blacklist",
                  help="Exclude tasks from particular lists. This option works the same way as the whitelist: \
                  conkyRTM.py -b Inbox -b Personal uname pass list_date \
                  would display all tasks EXCEPT those from your Inbox or your Personal list.")

parser.add_option("-t","--titlecolor",type="string",dest="titlecolor",default='',
                  help="For use with Conky.  Specify the color for the title.")

parser.add_option("-l","--listcolor",type="string",dest="listcolor",default='',
                  help="For use with Conky.  Specify the color for the list.")

parser.add_option("-a","--aligntitle",type="string",dest="titlealign",default='',
                  help="For use with Conky.  Specify the alignment of the title.")

parser.add_option("-g","--galignlist",type="string",dest="listalign",default='',
                  help="For use with Conky.  Specify the alignment of the list.")

(options, args) = parser.parse_args()



if len(args) != 3:
    parser.error("incorrect number of arguments")

# format listcolor for conky
if len(options.listcolor)>0:
    listcolor = '${color' + options.listcolor + '}'
else:
    listcolor = options.listcolor
    
# format titlecolor for conky
if len(options.titlecolor)>0:
    titlecolor = '${color' + options.titlecolor + '}'
else:
    titlecolor = options.titlecolor

# format titlealign for conky
if len(options.titlealign)>0:
    titlealign = '${' + options.titlealign + '}'
else:
    titlealign = options.titlealign

# format listalign for conky
if len(options.listalign)>0:
    listalign = '${' + options.listalign + '}'
else:
    listalign = options.listalign

# convenient names for the options
blacklist = options.blacklist
whitelist = options.whitelist



#required arguments
uname = args[0]
password = args[1]
list_date = args[2]


def get_feed():
    '''The method to do HTTPBasicAuthentication'''
    
    link = RTM + uname
    
    # Create an OpenerDirector with support for Basic HTTP Authentication...
    auth_handler = urllib.request.HTTPBasicAuthHandler()
    auth_handler.add_password(realm= 'RememberTheMilk Atom Feed',
                              uri= 'https://www.rememberthemilk.com/',
                              user= uname,
                              passwd= password)
    opener = urllib.request.build_opener(auth_handler)
    # ...and install it globally so it can be used with urlopen.
    urllib.request.install_opener(opener)
    response = urllib.request.urlopen(link)
    feed = response.read() 
    response.close()
    return feed

def getText(node):
    rc = ""
    for child in node.childNodes:
        if child.nodeType == child.TEXT_NODE:
            rc = rc + child.data
    return rc
    
def task_info(parsed,i):
    
    
    tasklist = parsed.getElementsByTagName('entry')
    
    task = tasklist[i]
    
    # get task title
    task_title = task.getElementsByTagName('title')
    title = getText(task_title[0])
    
    # get task contents
    contents_list = task.getElementsByTagName('content')
    task_contents = contents_list[0].getElementsByTagName('span')
    for span in task_contents:
        class_name = span.attributes['class']
        if class_name.value == 'rtm_due_value':
            date_raw = getText(span)
            try:
                date_parsed = datetime.strptime(date_raw, "%a %d %b %y")
            except ValueError:
                try:
                    date_parsed = datetime.strptime(date_raw, "%a %d %b %y at %I:%M%p")
                except ValueError:
                    date_parsed = datetime.today()
            task_due = date_parsed.date()
        if class_name.value == 'rtm_priority_value':
            task_priority = getText(span)
        if class_name.value == 'rtm_time_estimate_value':
            task_time = getText(span)
        if class_name.value == 'rtm_tags_value':
            task_tags = getText(span)
        if class_name.value == 'rtm_location_value':
            task_location = getText(span)
        if class_name.value == 'rtm_postponed_value':
            task_postponed = getText(span)
        if class_name.value == 'rtm_list_value':
            task_in_list = getText(span)
    
    # create dictionary with task info       
    task_info = {}
    task_info['title'] = title
    task_info['due'] = task_due
    task_info['priority'] = task_priority
    task_info['time'] = task_time
    task_info['tags'] = task_tags
    task_info['location'] = task_location
    task_info['postponed'] = task_postponed
    task_info['list'] = task_in_list
    
    return task_info
     
def convert_date(time):
    
    one_day = timedelta(days=1)
    today = date.today()
    tomorrow = today + one_day

    if time == 'today':
        day = today
    elif time == 'tomorrow':
        day = tomorrow
    else:
        day = today + (int(time) * one_day)
    return day
    
def get_tasks(feed, time,blacklist,whitelist):
    
    dom = parseString(feed)
    
    num_task = len(dom.getElementsByTagName('entry'))
    
    task_list = []
    
    # Run through all the task and grab the ones 
    # that match the desired due date.
    
    for m in range(0,num_task):
        
        task = task_info(dom,m) 
        
        # I used this line for testing
        # print(task['title'] + ' ' + str(task['due']) + ' ' + str(time))
        
        # if there is a whitelist grab only those tasks
        if len(whitelist)>0:
            whitelist = set(whitelist)
            if task['list'] in whitelist:
                  if str(task['due']) == str(time):
                    task_list.append(task)
                
        # if there is a blacklist only grab those tasks
        elif len(blacklist)>0:
            remove = (str(task['list']) in set(blacklist))
            if remove == False:
              if str(task['due']) == str(time):
                task_list.append(task)
            
        # if there is no whitelist or blacklist then just grab everything for 
        # the desired day
        else:
            if str(task['due']) == str(time):
                task_list.append(task)
            
    return task_list
    
    
if __name__ == "__main__":
    
    # Do auth and then get the feed, strip out garbage at the beginning and the 
    # end of the feed.
    taskfeed = get_feed()[6:-8]

    
    emptylist = []
    
    list_date = convert_date(list_date.lower())       
    
    if list_date == date.today():
        time_title = 'Today'
    elif list_date == date.today()+timedelta(days=1):
        time_title = 'Tomorrow'
    else:
        time_title = 'on ' + list_date.strftime('%a %Y-%m-%d')
    
    # Parse the feed and get grab the tasks with the desired due date.
    # Returns a list of tasks, the tasks are dictionary objects which contains
    # the task information.
    tasklist = get_tasks(taskfeed, list_date,options.blacklist,options.whitelist) 
    
    print(' '+titlealign+''+titlecolor+'Tasks Due ' + time_title + ':')
    for task in tasklist:
        print('    '+listalign+''+ listcolor + '' +task['title'] + '' + task['list'])
    if tasklist == emptylist:
        print('    '+listalign+''+listcolor+'Nothing Due')

```

Here's what happened when I tried to combine the multidays thing with the standard:
```

#!/usr/bin/python3
#
# ======================================================================
# Copyright (C) 2009 Lucas David-Roesler <roesler.lucas@gmail.com>
# Time-stamp: Tue January 20, 2009
# This program is free software; you can redistribute it and/or modify
# it under the terms of the GNU General Public License version 2 as
# published by the Free Software Foundation.
# ======================================================================
#
# This script accesses takes in the username, password, and a date then
# retrieves # and outputs the tasks due on that date from the users account at 
# http://www.rememberthemilk.com . The date can be input as Today, Tomorrow, or
# as an integer: 0 = Today, 1 = Tomorrow, 2 = Today + 2 days, etc.  
#
# This is intended to be used with conky: http://conky.sourceforge.net/ .
#
# Note that the username and password are not encrypted or obfruscated in any way.
#
# Currently any task that has a due date of never or an empty due date is
# treated as due today. The thought is that those tasks are meant to be constant
# reminders and therefore always displayed. In the future this may be given an
# option. 

import sys
import urllib.request
from optparse import OptionParser
from datetime import datetime, date, time, timedelta
from xml.dom.minidom import parse, parseString

RTM = 'https://www.rememberthemilk.com/atom/'
#whitelist = []
#blacklist = []
#titlecolor = ''
#listcolor = ''


# options
usage = "usage: %prog [options] uname pass list_date "
parser = OptionParser(usage)
parser.set_defaults(whitelist=[],blacklist=[],titlecolor='',listcolor='')
parser.add_option("-w","--whitelist", action="append",type='string',dest="whitelist",
                  help='Display only the tasks from specific lists. This option requires a separate instance for each list you want displayed. i.e. if you want to display only your inbox and your personal list use: \
                  conkyRTM.py -w Inbox -w Personal uname pass list_date')

parser.add_option("-b","--blacklist", action="append",type='string',dest="blacklist",
                  help="Exclude tasks from particular lists. This option works the same way as the whitelist: \
                  conkyRTM.py -b Inbox -b Personal uname pass list_date \
                  would display all tasks EXCEPT those from your Inbox or your Personal list.")

parser.add_option("-t","--titlecolor",type="string",dest="titlecolor",default='',
                  help="For use with Conky.  Specify the color for the title.")

parser.add_option("-l","--listcolor",type="string",dest="listcolor",default='',
                  help="For use with Conky.  Specify the color for the list.")


(options, args) = parser.parse_args()



if len(args) != 3:
    parser.error("incorrect number of arguments")

# format listcolor for conky
if len(options.listcolor)>0:
    listcolor = '${' + options.listcolor + '}'
else:
    listcolor = options.listcolor
    
# format titlecolor for conky
if len(options.titlecolor)>0:
    titlecolor = '${' + options.titlecolor + '}'
else:
    titlecolor = options.titlecolor

# convenient names for the options
blacklist = options.blacklist
whitelist = options.whitelist

uname = sys.argv[1]
password = sys.argv[2]
list_date = sys.argv[3]


def get_feed():
    '''The method to do HTTPBasicAuthentication'''
    
    link = RTM + uname
    
    # Create an OpenerDirector with support for Basic HTTP Authentication...
    auth_handler = urllib.request.HTTPBasicAuthHandler()
    auth_handler.add_password(realm= 'RememberTheMilk Atom Feed',
                              uri= 'https://www.rememberthemilk.com/',
                              user= uname,
                              passwd= password)
    opener = urllib.request.build_opener(auth_handler)
    # ...and install it globally so it can be used with urlopen.
    urllib.request.install_opener(opener)
    response = urllib.request.urlopen(link)
    feed = response.read() 
    response.close()
    return feed

def getText(node):
    rc = ""
    for child in node.childNodes:
        if child.nodeType == child.TEXT_NODE:
            rc = rc + child.data
    return rc
    
def task_info(parsed,i):
    
    
    tasklist = parsed.getElementsByTagName('entry')
    
    task = tasklist[i]
    
    # get task title
    task_title = task.getElementsByTagName('title')
    title = getText(task_title[0])
    
    # get task contents
    contents_list = task.getElementsByTagName('content')
    task_contents = contents_list[0].getElementsByTagName('span')
    for span in task_contents:
        class_name = span.attributes['class']
        if class_name.value == 'rtm_due_value':
            date_raw = getText(span)
            try:
                date_parsed = datetime.strptime(date_raw, "%a %d %b %y")
            except ValueError:
                try:
                    date_parsed = datetime.strptime(date_raw, "%a %d %b %y at %I:%M%p")
                except ValueError:
                    date_parsed = datetime.today()
            task_due = date_parsed.date()
        if class_name.value == 'rtm_priority_value':
            task_priority = getText(span)
        if class_name.value == 'rtm_time_estimate_value':
            task_time = getText(span)
        if class_name.value == 'rtm_tags_value':
            task_tags = getText(span)
        if class_name.value == 'rtm_location_value':
            task_location = getText(span)
        if class_name.value == 'rtm_postponed_value':
            task_postponed = getText(span)
    
    # create dictionary with task info       
    task_info = {}
    task_info['title'] = title
    task_info['due'] = task_due
    task_info['priority'] = task_priority
    task_info['time'] = task_time
    task_info['tags'] = task_tags
    task_info['location'] = task_location
    task_info['postponed'] = task_postponed
    
    return task_info
     
def convert_date(time):
    
    one_day = timedelta(days=1)
    today = date.today()
    tomorrow = today + one_day

    if time == 'today':
        day = today
    elif time == 'tomorrow':
        day = tomorrow
    else:
        day = today + (int(time) * one_day)
    return day
    
def get_tasks(feed, time,blacklist,whitelist):
    
    dom = parseString(feed)
    
    num_task = len(dom.getElementsByTagName('entry'))
    
    task_for_time = []
    
    # Run through all the task and grab the ones 
    # that match the desired due date.
    
    for m in range(0,num_task):
        
        task = task_info(dom,m) 
        
        # I used this line for testing
        # print(task['title'] + ' ' + str(task['due']) + ' ' + str(time))
        
        if str(task['due']) == str(time):
            task_for_time.append(task)
            
    return task_for_time
    
    
if __name__ == "__main__":
    
    # Do auth and then get the feed, strip out garbage at the beginning and the 
    # end of the feed.
    taskfeed = get_feed()[6:-8]

    
    emptylist = []
    
    days = list_date.split(',')
    for day in days:

        day = convert_date(day.lower())
    
        if day == date.today():
            time_title = 'Today'
        elif day == date.today()+timedelta(days=1):
            time_title = 'Tomorrow'
        else:
            time_title = 'on ' + day.strftime('%a, %b %d')
    
        # Parse the feed and get grab the tasks with the desired due date.
        # Returns a list of tasks, the tasks are dictionary objects which contains
        # the task information.
    tasklist = get_tasks(taskfeed,day) 
    
    print(' '+titlecolor+'Tasks Due ' + time_title + ':')
    for task in tasklist:
        print('    '+ listcolor + '' +task['title'] + '' + task['list'])
    if tasklist == emptylist:
        print('    '+listcolor+'Nothing Due')

```

So how do I do this RIGHT?

---

### Post by MusicMastaMike on 2009-02-19
Here's mine now with the working color options.  No time right now to try and combine with yours, but if you can't figure it out, let me know and I'll help.

---

### Post by TheAxeR on 2009-02-19
@ wynneth

Just taking a brief look at what you did the first thing that I notice that would cause issues is indenting.  Indenting is probably the most important part of python, it cares about white space.  In particular the code
```

tasklist = get_tasks(taskfeed,day) 
    
    print(' '+titlecolor+'Tasks Due ' + time_title + ':')
    for task in tasklist:
        print('    '+ listcolor + '' +task['title'] + '' + task['list'])
    if tasklist == emptylist:
        print('    '+listcolor+'Nothing Due')

```

should be indented one level so that it is within the for loop

```
 for day in days:
```

The other issues is that in Frankensteining the two different scripts together there are some... structural differences, I am not sure if that is the correct way of saying it, between the two scripts that do not mesh together well.  The first major example is the use of sys and the use of optparse. Techniqually in my version sys is not used infavor of optionpars which allows the things like the whitelist or the alignment that you added.  This caused an issue because when using optionparse the lines 
```

uname = sys.argv[1]
password = sys.argv[2]
list_date = sys.argv[3]

```

Need to be 
```

uname = args[0]
password = args[1]
list_date = args[2]

```

The last issue I found was in calling for the tasks

```

    tasklist = get_tasks(taskfeed,day)

```
needed to be
```

    tasklist = get_tasks(taskfeed,day,blacklist,whitelist) 

```

Please do not take the length of this as an insult.  I just figured I would be thorough. 

I made  corrections to what I found and have attached a working version ( or at least seemingly working :) ) 

The new usage should now be:
```

Usage: rtm_test.py [options] uname pass list_date 

Options:
  -h, --help            show this help message and exit
  -w WHITELIST, --whitelist=WHITELIST
                        Display only the tasks from specific lists. This
                        option requires a separate instance for each list you
                        want displayed. i.e. if you want to display only your
                        inbox and your personal list use:
                        conkyRTM.py -w Inbox -w Personal uname pass list_date
  -b BLACKLIST, --blacklist=BLACKLIST
                        Exclude tasks from particular lists. This option works
                        the same way as the whitelist:
                        conkyRTM.py -b Inbox -b Personal uname pass list_date
                        would display all tasks EXCEPT those from your Inbox
                        or your Personal list.
  -t TITLECOLOR, --titlecolor=TITLECOLOR
                        For use with Conky.  Specify the color for the title.
  -l LISTCOLOR, --listcolor=LISTCOLOR
                        For use with Conky.  Specify the color for the list.


list_date can be a comma separated list of the form: 0,1,2.  
This would give you a list for today, tomorrow, and the day after.

```

Note that this does not include your alignment options.  I'll let you try to add those in.

One thing to think about is how the alignment is supposed to work.  If you try to pass spaces as an option I do not believe that it will actually read them.  Additionally you do not need the curly braces like 
```
 
listalign = '${' + options.listalign + '}'

```
if you only intend to add spaces.  The dollar sign and curly braces are only necessary for conky commands, such as the colors.  My personal thoughts are to make two alignments, left and right, and pass a integer value as the option.  You could then somehow make python add that many more spaces to the the left or right end of the line.

For instance if you passed  -la or --lalign 5, python would add 5 spaces to the beginning of the line.

---

### Post by wynneth on 2009-02-20
K, will try in approx 8 hrs....zzzzzzzz

---

### Post by wynneth on 2009-02-20
Thanks. I dunno how I was screwing that up. Here's mine, which is yours plus individual options for alignment, font, and color for each secton (title, task, list).

---

### Post by wynneth on 2009-03-01
I'm cross posting this because it applies to conky in general, but I only now ran into it because of the Remember The Milk python script. Apparently, if you try to use a $ in your test conky automatically assumes it needs {} around it. It became a problem when I used dollar amounts on my remember the milk (i.e. PAY BILL $100) and conky outputs ${100}. At first I thought maybe it was just the script, but nope, seems to be conky in general. I'm sure it's some simple obvious thing, so what do I need to do for conky to display dollar signs without braces? I already figured out how to do a replace in the RTM python script to take care of it there, but I don't know what I need to replace $ with to fix it. Ideas? Knowledge?

---

### Post by TheAxeR on 2009-03-02
Maybe there is an escape character for it (don't know if that is the correct terminology).  For example in latex {} are invisible, they are used for grouping, in order to print {} you need to use \{ and \}.  I have not checked yet, just an idea.

---

### Post by wynneth on 2009-03-05
> **TheAxeR said:**
> Maybe there is an escape character for it (don't know if that is the correct terminology).  For example in latex {} are invisible, they are used for grouping, in order to print {} you need to use \{ and \}.  I have not checked yet, just an idea.
Yeah that was my thought. Tried the slashes first, tried html character sequences and unicode numbers too. I dunno.

---

### Post by wynneth on 2009-04-24
Well the Jaunty upgrade has created some new problems for the python n00b here....
```
Traceback (most recent call last):
  File "/home/wynneth/conky/conkyRTM.py", line 321, in <module>
    tasklist = get_tasks(taskfeed, day, options.blacklist, options.whitelist) 
  File "/home/wynneth/conky/conkyRTM.py", line 258, in get_tasks
    dom = parseString(feed)
  File "/usr/lib/python3.0/xml/dom/minidom.py", line 1945, in parseString
    return expatbuilder.parseString(string)
  File "/usr/lib/python3.0/xml/dom/expatbuilder.py", line 940, in parseString
    return builder.parseString(string)
  File "/usr/lib/python3.0/xml/dom/expatbuilder.py", line 223, in parseString
    parser.Parse(string, True)
xml.parsers.expat.ExpatError: not well-formed (invalid token): line 1, column 7

```

---

### Post by TheAxeR on 2009-04-24
This is an error that I ran into when I first wrote the script.  Originally ( in the first script ) when it downloaded the rss feed, there was some garbage characters that got attached to the feed and would interfere with the rss parser.  That is the error that you are seeing now.  The original fix is to strip out those garbage characters before feeding it to the rss parser.  This was done by truncating the beginning and the end of the rss feed since this is the only place where those garbage characters were occurring.

I ran into the this issue again when I updated to jaunty as well. It seems like they fixed whatever bug was going on previously.  Hence, when the script strips out the characters we are now breaking the feed.  

The solution is to remove the code that strips out the characters from the feed.  This code happens at approximately line 237 in my current script.

It looks like this
```

taskfeed = get_feed()[6:-8]

```

this code means to read the feed starting after the sixth character and ending eight characters from the end.  The new code should look like this:
```

taskfeed = get_feed()

```
This just reads the rss feed as is, no modifications. 

I attached my current version of the code.

---

### Post by wynneth on 2009-04-25
Excellent, thanks!

---

### Post by Jeff Carr on 2009-07-23
Wow, this works really great!

I renamed it to conkyRememberTheMilk.py, moved it to /usr/share/conkyrememberthemilk/ and created a simple bash script in /usr/bin/ for it.

```

#! /bin/sh
cd /usr/share/conkyrememberthemilk/
$PYTHON3PATH /usr/bin/python3 /usr/share/conkyrememberthemilk/conkyRememberTheMilk.py "$@"
```

With that I just run

```

${execi 900 conkyRememberTheMilk username password today}
```

and it works beautifully.  Just basic, but I thought I'd post it here for anyone who was learning.

---

### Post by asphixmx on 2010-09-19
Hi, I don't know python... do you think it's possible to print the tasks, instead of alphabetically, by grouping by list's names? I guess in this part:
    tasklist = get_tasks(taskfeed, list_date,options.blacklist,options.whitelist) 
    
    print(' '+titlecolor+'Tasks for ' + time_title + ':')
    for task in tasklist:
        print('    '+ listcolor + '' + task['list'] + ': ' + task['title'])
    if tasklist == emptylist:
        print('    '+listcolor+'Nothing Due')

the TASKLIST gets the feed like it is...maybe some lines to re-order TASKLIST by LIST.
Anyone know how to do this? I guess this could come in handy, to get the tasks grouped by list.

---

### Post by TheAxeR on 2010-09-22
I have stopped using conky and haven't really looked at the code recently.  I just took a quick look and it seems that it should be possible, but it does not look like it will be a one line fix.  Though don't take my word on that because I am not a python master. The issue is that the printed task list is a two level array and so I am not sure of the easiest way to reorder it.  An alternative would be to call the script several times for each list, but this is far from ideal.  Because school has started back up I am not sure when the I will next be able to look at it. Sorry.

---

### Post by asphixmx on 2010-09-22
Thanks for your answer. Well, you gave me the solution, calling the script each time for each "list". Since I have only two lists, it's easy. But as you said it is not ideal. I want to learn python; one of my projects will be to sort this array. If I can do it, I'll post this add to your script. Thanks again!.

---

### Post by poolek on 2010-11-18
This is great. Thanks for your work.

I use this to complement RTM CLI because it can't handle recurring tasks when returning today's list, but yours can. This to display my today todo list, and RTM CLI to add and manipulate my tasks = me very happy.

Here's the link for any interested:
[http://dwaring87.oos.cc/web/projects/rtm.html](http://dwaring87.oos.cc/web/projects/rtm.html)

---


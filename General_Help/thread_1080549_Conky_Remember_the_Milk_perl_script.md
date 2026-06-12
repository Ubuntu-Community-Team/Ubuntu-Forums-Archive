---
title: "Conky Remember the Milk perl script"
date: 2009-02-25
forum: General Help
---

### Post by MusicMastaMike on 2009-02-25
I first saw TheAxeR's python script [here]("http://ubuntuforums.org/showthread.php?p=6615155") and was playing around with that for awhile. I am not a great python programmer, so I wrote up a perl script to interact with RTM, and I include lots of options. If you are more comfortable with python, by all means use TheAxeR's script. This is just an alternative.

Run the script with no arguments to see options.

```

NAME
        conkyRTM.pl

SYNOPSIS
        conkyRTM.pl -u USER -p PASSWORD

DESCRIPTION
        Perl script to output a user's RTM tasks to Conky

        To use this in Conky, put something like this in your .conkyrc:
            ${execpi 3600 perl /path/to/conkyRTM.pl -u USER -p PASS [options]}

ARGUMENTS
        -u USER, --user=USER           Specifies the username to be used for RTM
        -p PASSWORD, --pass=PASSWORD   Specifies the password to be used for RTM

OPTIONS
        -d N, --days=N          Specifies how many days (N) to grab tasks for
        -t, --time              Show time task is due in output
        -e, --estimate          Show task's time estimate in output.
        -y, --priority          Show task's priority in output.
        -l, --location          Show task's location in output.
        --tcolor=COLOR          Specify color for tasks. COLOR can be given as a word,
                                i.e. blue, as hex, i.e. 0000ff, or as colorN as in Conky
        --hcolor=COLOR          Specify color for day headers. COLOR can be given as a word,
                                i.e. blue, as hex, i.e. 0000ff, or as colorN as in Conky
        --tindent=N             Specify number of spaces to indent tasks.
        --hindent=N             Specify number of spaces to indent day headers.
        --eindent=N             Specify number of spaces to indent extra task information,
                                i.e. location, estimate, or priority.
        -r, --alignr            Right-align output in Conky
        -c, --alignc            Center-align output in Conky
        -f FONT, --font=FONT    Specify font to be used for output. FONT should be in one of the
                                following formats:
                                   --> font_name
                                   --> font_name:size=SIZE
                                   --> :size=SIZE
                                NOTE: SIZE is an integer
        -n, --not-due           Include tasks without a due date in output
        -o, --overdue           Include overdue tasks
        --include-tags=TAGS     Include only tasks matching specified tags in output. TAGS is a
                                comma separated list, i.e. tag1,tag2,tag3.
        --ignore-tags=TAGS      Exclude all tasks matching specified tags from output. TAGS is a
                                comma separated list, i.e. tag1,tag2,tag3.
        --white-lists=LISTS     Include only tasks in specified lists in output. LISTS is a comma
                                separated list, i.e. list1,list2,list3.
        --black-lists=LISTS     Exclude all tasks in specified lists from output. LISTS is a comma
                                separated list, i.e. list1,list2,list3.
        --priorities=PRIORITIES Include only tasks matching specified priorities in output.
                                PRIORITIES is a comma separated list. Valid priorities are
                                pri1, pri2, pri3, none
        --no-headers            Don't show day headers.
        -l, --location          Show location of tasks in output
        --24-hour               Show due times in 24 hour format
        -h, --help              Print this text and exit
        -m, --man               Print full documentation

AUTHOR
        Michael Stegeman

LICENSE
        This program is free software: you can redistribute it and/or modify
        it under the terms of the GNU General Public License as published by
        the Free Software Foundation, either version 3 of the License, or
        (at your option) any later version.

        This program is distributed in the hope that it will be useful,
        but WITHOUT ANY WARRANTY; without even the implied warranty of
        MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
        GNU General Public License for more details.

        You should have received a copy of the GNU General Public License
        along with this program.  If not, see <http://www.gnu.org/licenses/>.

```

You can always find the newest version of this script here:
[http://github.com/mrstegeman/conkyRTM]("http://github.com/mrstegeman/conkyRTM")

---

### Post by cmorse on 2009-03-09
I just tried out your script and like the flexibility over using RSS for RTM events. (I didn't want to install Python3 right now and Perl is already there).

However anytime I try to invoke either black-list or white-list parameters I just get a 'No tasks due.', tags seem to work ok, but I'd rather segregate on the list and not worry about tagging all my entries to get them to show up in particular spots.  Specifically I'm using separate lists for home and work related tasks.

I don't see any obvious issues in the code, but I don't normally do any Perl scripting.  Any ideas?

---

### Post by MusicMastaMike on 2009-03-09
Good catch! There was an issue with when I was pushing hashes onto the array while parsing the XML data. It's fixed now. Let me know if you come across anything else.

The script in the main post has been re-uploaded.

---

### Post by cmorse on 2009-03-10
> **MusicMastaMike said:**
> The script in the main post has been re-uploaded.

and works quite fine... thank you!!

---

### Post by cmorse on 2009-03-13
Script working quite nicely, thanks.

Not really a bug, but a suggestion for an enhancement/tweak.  I have a separate section in my conky file for RTM tasks in my inbox - I have my database email tasks to my RTM and this provides me with an efficient heads up when a new task shows up.

But by default, new tasks in inbox don't have a due date set, therefore when I elect to show tasks with no due date and white-lists=inbox, I get an empty result for tasks due today, then an 'Other Tasks' entry with tasks to file.  

It would just be cleaner if there were a way to elect to display ONLY tasks without a due date, rather than including today tasks by default.  See my screenshot (bottom section) for clarification.

---

### Post by MusicMastaMike on 2009-03-13
> **cmorse said:**
> Script working quite nicely, thanks.

Not really a bug, but a suggestion for an enhancement/tweak.  I have a separate section in my conky file for RTM tasks in my inbox - I have my database email tasks to my RTM and this provides me with an efficient heads up when a new task shows up.

But by default, new tasks in inbox don't have a due date set, therefore when I elect to show tasks with no due date and white-lists=inbox, I get an empty result for tasks due today, then an 'Other Tasks' entry with tasks to file.  

It would just be cleaner if there were a way to elect to display ONLY tasks without a due date, rather than including today tasks by default.  See my screenshot (bottom section) for clarification.

Done. Keep the suggestions coming.

Updated script is in first post.

---

### Post by pauna on 2009-04-26
I tried your script and it barfs on scandinavian characters in task names. Everything after the first "odd" character is cut off. For example "Lisää" (meaning "to add") gets shown "Lis".

I'm not quite sure if this is a problem in your script, conky or RTM.

Yes, I have "override_utf8_locale yes" and I'm using xft fonts in my .conkyrc.

If you have any hints, please let me know.

---

### Post by MusicMastaMike on 2009-04-26
Can you try running the script in a terminal (use the same command and options as in your .conkyrc)?  Post the output here, please.  That will let us see if it's the script or conky.

---

### Post by MusicMastaMike on 2009-04-26
> **pauna said:**
> I tried your script and it barfs on scandinavian characters in task names. Everything after the first "odd" character is cut off. For example "Lisää" (meaning "to add") gets shown "Lis".

I'm not quite sure if this is a problem in your script, conky or RTM.

Yes, I have "override_utf8_locale yes" and I'm using xft fonts in my .conkyrc.

If you have any hints, please let me know.

Ah, forget the last post.  I got this fixed, the XML parser wasn't keeping the UTF-8 encoding. New script in first post.

---

### Post by pauna on 2009-05-01
Thanks, it works fine now.

---

### Post by pauna on 2009-05-01
How are overdue tasks available in this script? I have some overdue tasks and they are not visible when I select tasks based on days (for example 0,1 and 2) nor when I select tasks based on "not-due" option.

---

### Post by MusicMastaMike on 2009-05-02
> **pauna said:**
> How are overdue tasks available in this script? I have some overdue tasks and they are not visible when I select tasks based on days (for example 0,1 and 2) nor when I select tasks based on "not-due" option.

I was actually thinking about this the other day.  I've added a -o or --overdue option that will show your overdue tasks before anything else.  Check the first post for updated script.

---

### Post by pauna on 2009-05-03
Wow, you work fast, thanks!

---

### Post by pauna on 2009-05-03
There's a bug in the newest version of the script. The option letter "r" stands for two different options: align right and priority. This causes priorities to be displayed if align right is selected. Besides, align right doesn't work.

If you change the priority letter to let's say 'y', the problem goes away.

---

### Post by MusicMastaMike on 2009-05-04
> **pauna said:**
> There's a bug in the newest version of the script. The option letter "r" stands for two different options: align right and priority. This causes priorities to be displayed if align right is selected. Besides, align right doesn't work.

If you change the priority letter to let's say 'y', the problem goes away.

Good catch, fixed now.  Keep the comments coming!

---

### Post by DouglasCaixeta on 2009-05-12
Hi,

I'm having a problem to use it. Sorry, I'm new in Conky, but I already use to see my emails and temperatures.

1) What I did:

+ Add the following line on ~/conkyrc

```
${execpi 3600 perl ~/scripts/conkyRTM.pl -u <MYUSER> -p <MYPASS> [options]}
```

+ Put conkyRTM.pl in ~/scripts

2) The error:

Executing conky on a terminal, I receive the following error:

```
Can't locate Date/Calc.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.10.0 /usr/local/share/perl/5.10.0 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at /home/douglas/scripts/conkyRTM.pl line 30.
BEGIN failed--compilation aborted at /home/douglas/scripts/conkyRTM.pl line 30.
```


What should be the problem?

---

### Post by MusicMastaMike on 2009-05-12
> **DouglasCaixeta said:**
> Hi,

I'm having a problem to use it. Sorry, I'm new in Conky, but I already use to see my emails and temperatures.

1) What I did:

+ Add the following line on ~/conkyrc

```
${execpi 3600 perl ~/scripts/conkyRTM.pl -u <MYUSER> -p <MYPASS> [options]}
```

+ Put conkyRTM.pl in ~/scripts

2) The error:

Executing conky on a terminal, I receive the following error:

```
Can't locate Date/Calc.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.10.0 /usr/local/share/perl/5.10.0 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at /home/douglas/scripts/conkyRTM.pl line 30.
BEGIN failed--compilation aborted at /home/douglas/scripts/conkyRTM.pl line 30.
```


What should be the problem?

Try this in a terminal:

```
sudo apt-get install libdate-calc-perl
```

---

### Post by DouglasCaixeta on 2009-05-12
Hi,

Thank you MusicMastaMike. It works!

After installing libdate-calc-perl, I got the error:

> Can't locate DateTime/Format/Strptime.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.10.0 /usr/local/share/perl/5.10.0 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at /home/douglas/scripts/conkyRTM.pl line 31.
BEGIN failed--compilation aborted at /home/douglas/scripts/conkyRTM.pl line 31.

Then I installed the following:

libdatetime-set-perl
libdatetime-format-strptime-perl

Working!

---

### Post by DouglasCaixeta on 2009-05-12
Hi,

I have another question.

I used the option -n to show all the tasks. But it only shows 5 tasks, and the last one is cutted in the middle.
Is there a limit of characteres? How can I increase this?

---

### Post by somewhere2go on 2009-05-13
Sorry,

I'm having a problem to use it.

I Add the following line on ~/conkyrc:
```
${execpi 3600 perl /path/to/conkyrtm.pl --user=username --pass=mypassword --dates=0,1}
```

The script return:
```
Can't call method "strftime" on an undefined value at /usr/share/perl5/DateTime/Format/Strptime.pm line 570.
 at /path/to/conkyrtm.pl line 129
```

What should be the problem?

Thanks, in advance.

---

### Post by DouglasCaixeta on 2009-05-13
I think you have to install this package: libdatetime-format-strptime-perl

> sudo apt-get install libdatetime-format-strptime-perl

I was having a similar problem, see above.

---

### Post by somewhere2go on 2009-05-13
> **DouglasCaixeta said:**
> I think you have to install this package: libdatetime-format-strptime-perl



I was having a similar problem, see above.

Thanks, but i installed them all...
```
sudo apt-get install libdate-calc-perl, libdatetime-set-perl, libdatetime-format-strptime-perl
```
	
And the problem is the same.
What is wrong?

---

### Post by TheSeanKelly on 2009-06-07
I love your script!

I also have a couple of suggestions.

First, make overdue tasks show up by time.  In other words, currently if a task is due at 5:00pm on the 7th, It will not show up as overdue until 12am on the 8th.  Fix this so that the task will show as overdue as soon as 5:00pm has passed.  

Second, add an ability to not display titles for the given sections.  I modified your script and simply commented out the title output parts for my purposes.  The reasoning behind this is I wanted to have a to-do list of items that did not have any due date separate from tasks with a due date, but didn't want it to say "other tasks:" at the top of the list.

Sean

---

### Post by MusicMastaMike on 2009-06-07
> **DouglasCaixeta said:**
> Hi,

I have another question.

I used the option -n to show all the tasks. But it only shows 5 tasks, and the last one is cutted in the middle.
Is there a limit of characteres? How can I increase this?

Sorry for the delayed response.  Conky has a character limit.  Add the following to the top section of your .conkyrc:

```
text_buffer_size 1024
```

---

### Post by MusicMastaMike on 2009-06-07
> **TheSeanKelly said:**
> I love your script!

I also have a couple of suggestions.

First, make overdue tasks show up by time.  In other words, currently if a task is due at 5:00pm on the 7th, It will not show up as overdue until 12am on the 8th.  Fix this so that the task will show as overdue as soon as 5:00pm has passed.  

Second, add an ability to not display titles for the given sections.  I modified your script and simply commented out the title output parts for my purposes.  The reasoning behind this is I wanted to have a to-do list of items that did not have any due date separate from tasks with a due date, but didn't want it to say "other tasks:" at the top of the list.

Sean

I like the overdue tasks idea.  I'll work on that.  Also, the second suggestion should be an easy modification.  I'll post back when it's done.  Should be done today sometime.

---

### Post by MusicMastaMike on 2009-06-09
> **MusicMastaMike said:**
> I like the overdue tasks idea.  I'll work on that.  Also, the second suggestion should be an easy modification.  I'll post back when it's done.  Should be done today sometime.

Ok, sorry I took so long with this.  The script has been updated with both of your requests.  Let me know of any other suggestions/bugs, please.

---

### Post by TheSeanKelly on 2009-06-22
Mike

Thanks for your work!  

I have another suggestion, if you feel so inclined (please note that these suggestions are not things I'm necessarily dying to have implemented, but just suggestions, so feel no need to do them immediately!)

But my previously mentioned suggestion would be for tasks with a due date, do not display the day at all if there are no tasks due.  That way, if you have a task due on Monday and the next tuesday, you can see them both without rows and rows of "tuesday...no tasks due...wednesday...no tasks due...etc." 

Does that make sense?
Sean

---

### Post by TheSeanKelly on 2009-06-22
Mike

I actually made the change myself in a brute-force fashion since I don't need the script to work any other way.  It might be nicer to add an option to do this, but I didn't feel the need to do that, mostly because I haven't worked with perl too much.  Maybe I'll look into that.

I just axed the entire If block that assigns "no tasks due", and set the date to a variable in the beginning instead of printing it, and concatenated the date to the front of the string built in the loop.  Looks the same, except now nothing shows up if there are no tasks on the given day.

Uploaded as .txt instead of .pl because the forum wouldn't let me upload a .pl for whatever reason...

Sean

EDIT:  I just noticed that this screws up when there are multiple events on a given day.  I'm on this.

EDIT2:  And fixed.  Just added a conditional to check if $count is 1 before adding the date to the string (only do it the first time.)  Corrected script is up.

---

### Post by MusicMastaMike on 2009-06-23
Thanks for doing that!  I committed your changes to svn.

---

### Post by TheSeanKelly on 2009-06-24
> **MusicMastaMike said:**
> Thanks for doing that!  I committed your changes to svn.

Oh man!  I'm official now...

---

### Post by a.weiberjager on 2009-12-05
> **somewhere2go said:**
> Thanks, but i installed them all...
```
sudo apt-get install libdate-calc-perl, libdatetime-set-perl, libdatetime-format-strptime-perl
```
	
And the problem is the same.
What is wrong?

Yeah, I did the same thing, and I'm still having the same problem as you do, but in line 33.

Help, anybody?

---

### Post by asphixmx on 2010-09-19
Hi Mike, thanks for your script.
I can't get it work. After running it on conky, a line appears:

Can't call method "clone" on an undefined value at /usr/share/perl5/DateTime/Format/Strptime.pm line 589.

Line 585-590 in Strptime.pm are:

sub format_datetime {
    my ( $self, $dt ) = @_;
    my $pattern = $self->pattern;
    $pattern =~ s/%O/$dt->time_zone->name/eg;
	return $dt->clone->set_locale($self->locale)->strftime($pattern);
}

what could be the problem?

Thanks for your response

---

### Post by MusicMastaMike on 2010-09-20
> **asphixmx said:**
> Hi Mike, thanks for your script.
I can't get it work. After running it on conky, a line appears:

Can't call method "clone" on an undefined value at /usr/share/perl5/DateTime/Format/Strptime.pm line 589.

Line 585-590 in Strptime.pm are:

sub format_datetime {
    my ( $self, $dt ) = @_;
    my $pattern = $self->pattern;
    $pattern =~ s/%O/$dt->time_zone->name/eg;
	return $dt->clone->set_locale($self->locale)->strftime($pattern);
}

what could be the problem?

Thanks for your response

Seems to be a problem with the Perl module, rather than my script.  Try updating to the latest versions of both Perl and DateTime::Format::Strptime.  I'm running Perl 5.12.1 and DateTime::Format::Strptime 1.4000, and all is working fine.

---

### Post by maarts on 2010-10-21
> 

[I]Hi Mike, thanks for your script.
I can't get it work. After running it on conky, a line appears:

Can't call method "clone" on an undefined value at /usr/share/perl5/DateTime/Format/Strptime.pm line 589.

Line 585-590 in Strptime.pm are:

sub format_datetime {
    my ( $self, $dt ) = @_;
    my $pattern = $self->pattern;
    $pattern =~ s/%O/$dt->time_zone->name/eg;
    return $dt->clone->set_locale($self->locale)->strftime($pattern);
}

what could be the problem?

Thanks for your response[/I]

                                 Seems to be a problem with the Perl module, rather than my script.   Try updating to the latest versions of both Perl and  DateTime::Format::Strptime.  I'm running Perl 5.12.1 and  DateTime::Format::Strptime 1.4000, and all is working fine.     



Hi MusicMastaMike,

I have the same problem like asphixmx. I updated to perl 5.12.1 and DateTime::Format::Strptime 1.5000, but the problem couldn't be solved.

What can I do?

Thanks
maarts

---

### Post by MusicMastaMike on 2010-10-21
> **maarts said:**
> Hi MusicMastaMike,

I have the same problem like asphixmx. I updated to perl 5.12.1 and DateTime::Format::Strptime 1.5000, but the problem couldn't be solved.

What can I do?

Thanks
maarts

Can you put some debugging info in the script and see what it's trying to parse?  There is an if block in the "entry" function where format_datetime is called 4 times.  Put something like the following above that if block so we can see what it's failing on.
```
elsif ($entry->tag() eq "span") {
    if ($entry->att("class") eq "rtm_due_value") {
        $due = $entry->text();

        print "$due\n"; # ADD THIS LINE

        # Check for full due date, with time
        if ($due =~ /:/) {
```

---

### Post by maarts on 2010-10-22
Hi MusicMastaMike,

thanks for your reply.

The problem:

> 

Can't call method "clone" on an undefined value at /home/xxx/perl5/perlbrew/perls/perl-5.12.1/lib/site_perl/5.12.1/DateTime/Format/Strptime.pm line 781.
 at /media/xxx/conkyRTM.pl line 138

# Parse atom feed
my $twig = new XML::Twig(keep_encoding => 1, twig_handlers => { entry => \&entry });
my $tree = $twig->parse($xml); <<<----- here is the problem

maarts

---

### Post by MusicMastaMike on 2010-10-22
> **maarts said:**
> Hi MusicMastaMike,

thanks for your reply.

The problem:

maarts

$xml is guaranteed to be defined there. The parse function uses the entry callback function on every <entry> tag in the XML. Therefore, the error is in the entry function. Please add the debugging code I showed above.

---

### Post by maarts on 2010-10-22
Hi MusicMastaMike,

I added the line:

> 
print "$due\n"; # ADD THIS LINE



but I couldn't see an output in the terminal, see my conkyRTM.

Thanks
maarts

---

### Post by MusicMastaMike on 2010-10-22
> **maarts said:**
> Hi MusicMastaMike,

I added the line:



but I couldn't see an output in the terminal, see my conkyRTM.

Thanks
maarts

Try changing line 197 from
```
elsif ($due eq "never") {
```
to
```
elsif ($due eq "never" or $due eq '') {
```
and see if that fixes your problem.  It looks like the due date is not defined for some reason.

---

### Post by maarts on 2010-10-22
Hi MusicMastaMike,

unfortunately the problem ist still there. But I see the first date, look at my screenshot.

> 
Do 31. Dez 2009
Can't call method "clone" on an undefined value at /home/xxx/perl5/perlbrew/perls/perl-5.12.1/lib/site_perl/5.12.1/DateTime/Format/Strptime.pm line 781.
 at /xxx/datmar/files_markusch/Programmierung/PROJEKTE_SVN/CONKY/conkyRTM.pl line 138

Thanks,
maarts

---

### Post by MusicMastaMike on 2010-10-22
> **maarts said:**
> Hi MusicMastaMike,

unfortunately the problem ist still there. But I see the first date, look at my screenshot.

Thanks,
maarts

Ah, I see why now.  You will need to modify the definitions of $strp1 and $strp2 at lines 112 and 114 to meet your date's format. Remember the Milk apparently formats dates differently for other locales. Update those format strings and your problem should be fixed.

---

### Post by maarts on 2010-10-23
Hi MusicMastaMike,

ok, I solved the problem for the de_DE locale:

1.
```

# Long date format from atom feed -- DON'T CHANGE!!
$strp1 = new DateTime::Format::Strptime(pattern => '%a %d. %b %Y %H:%M', locale => 'de_DE',time_zone => 'Europe/Berlin', on_error => 'croak');
# Short date format from atom feed -- DON'T CHANGE!!
$strp2 = new DateTime::Format::Strptime(pattern => '%a %d. %b %Y', locale => 'de_DE', time_zone => 'Europe/Berlin', on_error => 'croak');

```2.
```

...
$due = $entry->text();
$due =~ s/\s/. /;        #<----- Add this line
...

```3.
```

...
elsif ($due eq "Niemals" or $due eq '') { #<---- "never" to "Niemals"
                    $delta = "inf";
                    $due = "none";
...

```Thanks for your help!
maarts

---

### Post by MusicMastaMike on 2010-10-23
> **maarts said:**
> Hi MusicMastaMike,

ok, I solved the problem for the de_DE locale:

1.
```

# Long date format from atom feed -- DON'T CHANGE!!
$strp1 = new DateTime::Format::Strptime(pattern => '%a %d. %b %Y %H:%M', locale => 'de_DE',time_zone => 'Europe/Berlin', on_error => 'croak');
# Short date format from atom feed -- DON'T CHANGE!!
$strp2 = new DateTime::Format::Strptime(pattern => '%a %d. %b %Y', locale => 'de_DE', time_zone => 'Europe/Berlin', on_error => 'croak');

```2.
```

...
$due = $entry->text();
$due =~ s/\s/. /;        #<----- Add this line
...

```3.
```

...
elsif ($due eq "Niemals" or $due eq '') { #<---- "never" to "Niemals"
                    $delta = "inf";
                    $due = "none";
...

```Thanks for your help!
maarts

Glad you got it figured out!

---


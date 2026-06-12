---
title: "Bash Script Question!"
date: 2006-07-28
forum: Desktop Environments
---

### Post by latebeat on 2006-07-28
Hi there,
I'm quite new to linux and I'm starting to find my way in writing my own scripts :D
I'm trying to write a script to send a particular email message to a small mailing list. 
The subject of the emails contains basic HTLM formatting and I want to pass the subject as a variable. However I can't use a variable with multiple lines for e.g.

MESSAGE="<HTM>
..
...
..."

and then call $MESSAGE...
what I do now is write everything across the same line: MESSAGE="<HTML>.. ... ...."
Is there anyway to do it the first way? I'm asking because even with a small message the variable is 340 columns long and it's not very easy to read or change.

any help is greately appreciated!

---

### Post by hw-tph on 2006-07-28
Well, the fine things about doing HTML with bash scripts is that line breaks doesn't really mean anything to the rendered HTML. :)

You can use backslashes to break up the HTML message into multiple lines. Just put a backslash at the end of each line:
```
message="<htm> \
bleh blah blah blooh \
foo \
bar \
baz"
```

Also consider using a [here document](http://www.tldp.org/LDP/abs/html/here-docs.html) instead, if applicable to your situation. It looks quite odd but is actually quite tidy and very useful. If you haven't done so already, check out the Advanced Bash Scripting Guide (which the link I provided is from).


Håkan

---

### Post by latebeat on 2006-07-28
> **hw-tph said:**
> Well, the fine things about doing HTML with bash scripts is that line breaks doesn't really mean anything to the rendered HTML. :)

You can use backslashes to break up the HTML message into multiple lines. Just put a backslash at the end of each line:
```
message="<htm> \
bleh blah blah blooh \
foo \
bar \
baz"
```

Also consider using a [here document](http://www.tldp.org/LDP/abs/html/here-docs.html) instead, if applicable to your situation. It looks quite odd but is actually quite tidy and very useful. If you haven't done so already, check out the Advanced Bash Scripting Guide (which the link I provided is from).


Håkan


Thanks for the quick reply, it was really so simple that makes me feel stupid! hehe! :)
I am reading the guide but it's huge and I'm progressing slowly so I did a quick and dirty solution that works and now I'm in the process of tidying up and hence my post.

Now I thought of making a seperate text file with the html text however I'm not sure if that would work mainly because in the html email I use variables that are expanded as strings taken from the script. For eg.

FILE=file1-todaysdate

and then call that within the html email as $FILE.

If I used a seperate html file would the variable $FILE be expanded as file1-todaysdate as the script would load the seperate file with the html code or would it be left unchanged as "$FILE" ?

and again, thanks! :D

---

### Post by latebeat on 2006-07-28
Bummer :(

---

### Post by Tomosaur on 2006-07-28
Your problems would be much easier to diagnose if you posted your script on here. It's very difficult to understand what people mean when they're talking about their own code unless you can actually see it in front of you, and that way we can suggest different things to help you out.

---

### Post by latebeat on 2006-07-28
I know what you're saying but my question is really simple though.
I've got two files:

1. say the script with 2 VARIABLES:
 a) DATE=currentdate
 b) MESSAGE=here to document to html email file

2. the here document with the HTML email text

Now if I need to evaluate the time within my HTML email with the email message IN the script I'd use $DATE and that would be no problem.
However If I pass the message to the script with a "here document" containing the $DATE variable will it parse it as the current date or will it parse it unchanged as "$DATE" as the scripts loads the external file ?

---


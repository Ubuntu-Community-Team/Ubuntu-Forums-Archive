---
title: "repeated messages in evolution: delete"
date: 2005-12-05
forum: Desktop Environments
---

### Post by foolosophy on 2005-12-05
Hi, I've just finished migrating all my e-mail from Outlook 2000 to Evolution 2.4.1 and have a little inconvinience.

I find that many of my messages were imported twice or even three times [SIZE="2"](probably because they were there from the beggining in my old database, or because I copied it twice.. dunno.. or... that I think about it, probably is due to sync problems whenever I had to download heavy mail from the server and somewhy it hanged up, and had to do all the dowloading again..)[/SIZE]

It doesn't matter WHY. What I'd like to know is.. can you think of anything I can do to delete repeated messages with some kind of "rule" or batch that does all the checking instead of having to select each one of them individually with the mouse? There are thousands of messages, so it would be a pain in the neck to do that.. supposedly, coomputers should do all the tedious work (ha!).

Thanks a lot,

Pablo@Ubuntu 5.10

---

### Post by foolosophy on 2005-12-06
I found something that may help (thanks to the people in evoltion IRC channel). 

[http://lists.ximian.com/archives/public/evolution/2005-January/041442.html]("http://lists.ximian.com/archives/public/evolution/2005-January/041442.html")

I tried it in my machine and didn't work. (The script runned, but it didn't detect repeated messages.. maybe because they weren't EXACTLY the same, because I had them repeated because I had imported them from Outlook, and also Evolution had imported them all again from the POP3 server).

I ended up doing it manually, but I left this to anyone that may find it useful.

Just in case the link falls down, here's the script, by Dan Jones (ddjones@riddlemaster.org).

-----------------------
You just have to copy it and paste it into a new file called "rdbox.pl", then make it executable, and run

perl rdbox.pl -u

there it will output the command-line options.
code follows:
---------------------------
```
#!/usr/bin/perl

use strict;
use warnings;

use Digest::MD5 qw(md5);
use Getopt::Long;

#SUB DECLARATIONS
sub ProcFile($);
sub ProcDirectory($);
sub ProcMessage($);
sub PrintUsage();

#GLOBAL VARIABLES
my (%MessageStore, $FileWrites);

#COMMANDLINE ARGUMENTS
my (@directories, @files);
my $recurse = '';
my $verbose = '';
my $usage = '';
my $global = '';

my $result = GetOptions("directory=s" => \@directories,
                                                "file=s" => \@files,
                                                "recurse" => \$recurse,
                                                "verbose" => \$verbose,
                                                "usage" => \$usage,
                                                "global" => \$global);


my $GoodArg = 0;
if(@files)
{
        $GoodArg = 1;
        for(@files)
        {
                ProcFile($_);
        }
}

if(@directories)
{
        $GoodArg = 1;
        for(@directories)
        {
                ProcDirectory($_);
        }
}

if(@ARGV)
{
        $GoodArg = 1;
        for(@ARGV)
        {
                ProcFile($_);
        }
}

PrintUsage() unless $GoodArg;

sub ProcFile($) 
{
        my $mbox = shift;
 
        print "Processing file $mbox\n";
        open MAILBOX, "<$mbox" or die "Can't open $mbox\n";
        open CLEAN, ">$mbox.clean" or die "Can't open $mbox.clean\n";
 
        %MessageStore = () unless $global;
 
        $FileWrites = 0;
 
        local $/ = "\n\nFrom ";

        my $Counter = 1;
        $_ = <MAILBOX>;
        $_ =~ s/\n\nFrom $//;
        ProcMessage($_);
        #print "Processed Message \#$Counter\n";
 
        while(<MAILBOX>) 
        {
                $Counter++;
                $_ =~ s/\n\nFrom $//;
                ProcMessage("\n\nFrom $_");
                print "Processed Message \#$Counter\n" if $verbose;
        }

        close MAILBOX;
        close CLEAN;
}

sub ProcDirectory($)
{
        my $directory = shift;
 
        chdir $directory or die "Can't change to directory $directory
\n";
 
        opendir DIRECTORY, $directory or die "Can't open directory 
$directory
\n";
        my @DirList = grep !/^\.\.?$/, readdir DIRECTORY;
        for(@DirList)
        {
                if(-d)
                {
                        print "Found directory $_\n" if $verbose;
                        if($recurse) 
                        {
                                ProcDirectory("$directory/$_");
                                chdir $directory;
                        }
                }
                elsif(/(.*)\.ibex\.index$/){
                        print "Found file $1\n" if $verbose;
                        ProcFile($1);
                }
        }
        print "\n";
}

sub ProcMessage($)
{
        my $Message = shift;
        my @MessageParts;
        my $HashValue;
        my $MessageId;
 
        my $InitWS;
        my $WSLength;
 
        $Message =~ /^(\s+)/;
        $InitWS = $1;
 
        $WSLength = 0;
        if($InitWS) {
                $Message =~ s/$InitWS//;
                $WSLength = length $InitWS;
        }
 
        @MessageParts = split /\n\n/, substr($Message, $WSLength), 2;
        unless($MessageParts[1])
        {
                print "Error in message!\n$Message\n\n";
                return;
        }
 
        $HashValue = md5($MessageParts[1]);
 
        $MessageParts[0] =~ /Message-I[dD]: (.*)/;
        $MessageId = $1;
 
        unless($MessageId)
        {
                print STDERR "Can't find Id in this 
message:\n$MessageParts[0]";
                return;
        }
 
        if(exists $MessageStore{$MessageId}) 
        {
                if($MessageStore{$MessageId} eq $HashValue)
                {
                        print "Found dupe of MessageID $MessageId!\n"
if 
$verbose;
                }
                else
                {
                        print CLEAN $Message;
                        print "False positive of $MessageId" if
$verbose;
                }
        }
        else
        {
                $MessageStore{$MessageId} = $HashValue;
                unless ($FileWrites) {
                        $Message =~ s/^\n+//;
                }
                print CLEAN $Message;
                $FileWrites++;
                print "Storing Message number $FileWrites, ID#: 
$MessageId\n" if
$verbose;
        }
}

sub PrintUsage() {
 
print <<USAGE;
rdbox - utility to remove duplicates from mbox files.
usage: rdbox [options] filename
       rdbox [options] -d directoryname

options:
        -d/-directory   name of directory containing mbox files

        -r/-recurse     recurses subdirectories below
 
        -u/-usage               print this message
 
        -f/-file                name of mbox files[s]
 
        -v/-verbose             print extra messages
 
        -g/-global              check for duplicates across all
mailboxes
 
USAGE
}
```

-------------------

---


---
title: "Trouble sending output into a text file"
date: 2009-05-19
forum: General Help
---

### Post by jonnythan on 2009-05-19
For some reason, I can't send the console output of a script to a file.

Something like this works fine:

ls -al >> /var/log/ls.log

But this doesn't:

./tools/run-periodic-tasks -verbose >> /var/log/mt.log

I can't seem to figure out why. Here's the contents of the script if it matters:

```
#!/usr/bin/perl -w

# Movable Type (r) (C) 2001-2009 Six Apart, Ltd. All Rights Reserved.
# This code cannot be redistributed without permission from www.sixapart.com.
# For more information, consult your Movable Type license.
#
# $Id: run-periodic-tasks 3455 2009-02-23 02:29:31Z auno $

use strict;

use lib 'lib', '../lib';

my $daemonize = 0;
my $sleep     = 5;
my $help      = 0;
my $load      = 10;
my $verbose   = 0;
my $scoreboard;
my $randomize_jobs = 0;
my $trace_objects = 0;

require Getopt::Long;
Getopt::Long::GetOptions(
    "daemon"       => \$daemonize,
    "sleep=i"      => \$sleep,
    "load=i"       => \$load,
    "scoreboard=s" => \$scoreboard,
    "randomly"     => \$randomize_jobs,
    "verbose"      => \$verbose,
    "leak"         => \$trace_objects,
);

if ( $trace_objects ) {
    require Devel::Leak::Object;
    Devel::Leak::Object->import( qw{ GLOBAL_bless } );
}

my %cfg;
$cfg{verbose} = $verbose;
$cfg{scoreboard} = $scoreboard;
$cfg{prioritize} = 1;
$cfg{randomize} = $randomize_jobs;

require MT::Bootstrap;
require MT;

my $mt = MT->new() or die MT->errstr;

$mt->{vtbl} = { };
$mt->{is_admin} = 0;
$mt->{template_dir} = 'cms';
$mt->{user_class} = 'MT::Author';
$mt->{plugin_template_path} = 'tmpl';
$mt->run_callbacks('init_app', $mt);

my $client = eval {
    require MT::TheSchwartz;
    my $c = MT::TheSchwartz->new(%cfg);
    no warnings 'once';
    $TheSchwartz::FIND_JOB_BATCH_SIZE = $load;
    $c;
};
if ((my $error = $@) && $verbose) {
    print STDERR "Error initializing TheSchwartz: $error\n";
}

if ($daemonize && $client) {
    $client->work_periodically($sleep);
} else {
    # First, run periodic tasks
    $mt->run_tasks();
    $client->work_until_done if $client;
}

1;

```

---

### Post by ActiveFrost on 2009-05-20
```
./tools/run-periodic-tasks -verbose
```
What this would output without sending it to text file ?

---

### Post by maheshasolkar on 2009-05-20
At least one print in the script is to STDERR. You might want to try:

C-SHELL:

  ./tools/run-periodic-tasks -verbose >>& /var/log/mt.log

BASH:

  ./tools/run-periodic-tasks -verbose 2>&1 >> /var/log/mt.log

---

### Post by FIONEX on 2009-05-20
Bro, there's a difference between an stderror output and stdout output.

echo "test" > file.txt; #Always works
print STDERR "test" > file.txt; # File is always empty

the  '>' only redirects standard output.
use '2>' to redirect error output.

so, '2>&1' means that you send STDERR to the same place that STDOUT is going to

---

### Post by geirha on 2009-05-20
> **maheshasolkar said:**
> BASH:
  ./tools/run-periodic-tasks -verbose 2>&1 >> /var/log/mt.log

No, that's the wrong order. This should work:
```
./tools/run-periodic-tasks -verbose >>/var/log/mt.log 2>&1 
```

See [http://tldp.org/LDP/abs/html/io-redirection.html](http://tldp.org/LDP/abs/html/io-redirection.html)

---

### Post by jonnythan on 2009-05-20
> **ActiveFrost said:**
> ```
./tools/run-periodic-tasks -verbose
```
What this would output without sending it to text file ?

Something like "Scwartz found 0 work" or a few lines about updating a blog feed.

---

### Post by jonnythan on 2009-05-20
> **geirha said:**
> No, that's the wrong order. This should work:
```
./tools/run-periodic-tasks -verbose >>/var/log/mt.log 2>&1 
```

See [http://tldp.org/LDP/abs/html/io-redirection.html](http://tldp.org/LDP/abs/html/io-redirection.html)

That seems to work perfectly, thank you.

---


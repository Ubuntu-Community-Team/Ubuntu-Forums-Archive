---
title: "How do i install &amp; configure perl on ubuntu 8.10 apache2"
date: 2009-03-07
forum: General Help
---

### Post by smooch101 on 2009-03-07
how do i install perl using cgi-bin and apache2 on ubuntu 8.10 and configure it.

Thanks in advance :KS

---

### Post by smooch101 on 2009-03-07
update:

i have looked in the cgi-bin in ubuntu but any pl scripts dont exucute

---

### Post by smooch101 on 2009-03-07
Please help

---

### Post by smooch101 on 2009-03-08
please help

---

### Post by ju2wheels on 2009-03-08
You most likely already have perl installed but here is the install command:

```

sudo apt-get install perl

```

To enable the cgi module:

```

sudo a2enmod cgi

```

To check that it is enabled check in /etc/apache2/sites-enabled/000-default and look for the following lines:

```

ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
<Directory "/usr/lib/cgi-bin">
	AllowOverride None
	Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
	Order allow,deny
	Allow from all
</Directory>

```

In order to add cgi files, save them in /usr/lib/cgi-bin/ (you will most likely need to use sudo to copy the files there) and *not* /var/www/cgi-bin/ . Once you have the files there you open [http://localhost/cgi-bin/your_cgi_file.pl](http://localhost/cgi-bin/your_cgi_file.pl)

---

### Post by smooch101 on 2009-03-08
> **ju2wheels said:**
> You most likely already have perl installed but here is the install command:

```

sudo apt-get install perl

```

To enable the cgi module:

```

sudo a2enmod cgi

```

To check that it is enabled check in /etc/apache2/sites-enabled/000-default and look for the following lines:

```

ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
<Directory "/usr/lib/cgi-bin">
	AllowOverride None
	Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
	Order allow,deny
	Allow from all
</Directory>

```

In order to add cgi files, save them in /usr/lib/cgi-bin/ (you will most likely need to use sudo to copy the files there) and *not* /var/www/cgi-bin/ . Once you have the files there you open [http://localhost/cgi-bin/your_cgi_file.pl](http://localhost/cgi-bin/your_cgi_file.pl)


Thanks but i dont think it is working
```
#!/usr/bin/perl

##############################################################################

# FormMail                        Version 1.92                               #

# Copyright 1995-2002 Matt Wright mattw@scriptarchive.com                    #

# Created 06/09/95                Last Modified 04/21/02                     #

# Matt's Script Archive, Inc.:    http://www.scriptarchive.com/              #

##############################################################################

# COPYRIGHT NOTICE                                                           #

# Copyright 1995-2002 Matthew M. Wright  All Rights Reserved.                #

#                                                                            #

# FormMail may be used and modified free of charge by anyone so long as this #

# copyright notice and the comments above remain intact.  By using this      #

# code you agree to indemnify Matthew M. Wright from any liability that      #

# might arise from its use.                                                  #

#                                                                            #

# Selling the code for this program without prior written consent is         #

# expressly forbidden.  In other words, please ask first before you try and  #

# make money off of my program.                                              #

#                                                                            #

# Obtain permission before redistributing this software over the Internet or #

# in any other medium. In all cases copyright and header must remain intact. #

##############################################################################

# ACCESS CONTROL FIX: Peter D. Thompson Yezek                                #

#                     http://www.securityfocus.com/archive/1/62033           #

##############################################################################

# Define Variables                                                           #

#      Detailed Information Found In README File.                            #



# $mailprog defines the location of your sendmail program on your unix       #

# system. The flags -i and -t should be passed to sendmail in order to       #

# have it ignore single dots on a line and to read message for recipients    #



$mailprog = '/usr/lib/sendmail -i -t';



# @referers allows forms to be located only on servers which are defined     #

# in this field.  This security fix from the last version which allowed      #

# anyone on any server to use your FormMail script on their web site.        #



@referers = ('wippetau.com','http://www.wippetau.com','www.wippetau.com','http://wippetau.com');



# @recipients defines the e-mail addresses or domain names that e-mail can   #

# be sent to.  This must be filled in correctly to prevent SPAM and allow    #

# valid addresses to receive e-mail.  Read the documentation to find out how #

# this variable works!!!  It is EXTREMELY IMPORTANT.                         #

@recipients = &fill_recipients(@referers);



# ACCESS CONTROL FIX: Peter D. Thompson Yezek                                #

# @valid_ENV allows the sysadmin to define what environment variables can    #

# be reported via the env_report directive.  This was implemented to fix     #

# the problem reported at http://www.securityfocus.com/bid/1187              #



@valid_ENV = ('REMOTE_HOST','REMOTE_ADDR','REMOTE_USER','HTTP_USER_AGENT');



# Done                                                                       #

##############################################################################



# Check Referring URL

&check_url;



# Retrieve Date

&get_date;



# Parse Form Contents

&parse_form;



# Check Required Fields

&check_required;



# Send E-Mail

&send_mail;



# Return HTML Page or Redirect User

&return_html;



# NOTE rev1.91: This function is no longer intended to stop abuse, that      #

#    functionality is now embedded in the checks made on @recipients and the #

#    recipient form field.                                                   #



sub check_url {



    # Localize the check_referer flag which determines if user is valid.     #

    local($check_referer) = 0;



    # If a referring URL was specified, for each valid referer, make sure    #

    # that a valid referring URL was passed to FormMail.                     #



    if ($ENV{'HTTP_REFERER'}) {

        foreach $referer (@referers) {

            if ($ENV{'HTTP_REFERER'} =~ m|https?://([^/]*)$referer|i) {

                $check_referer = 1;

                last;

            }

        }

    }

    else {

        $check_referer = 1;

    }



    # If the HTTP_REFERER was invalid, send back an error.                   #

    if ($check_referer != 1) { &error('bad_referer') }

}



sub get_date {



    # Define arrays for the day of the week and month of the year.           #

    @days   = ('Sunday','Monday','Tuesday','Wednesday',

               'Thursday','Friday','Saturday');

    @months = ('January','February','March','April','May','June','July',

               'August','September','October','November','December');



    # Get the current time and format the hour, minutes and seconds.  Add    #

    # 1900 to the year to get the full 4 digit year.                         #

    ($sec,$min,$hour,$mday,$mon,$year,$wday) = (localtime(time))[0,1,2,3,4,5,6];

    $time = sprintf("%02d:%02d:%02d",$hour,$min,$sec);

    $year += 1900;



    # Format the date.                                                       #

    $date = "$days[$wday], $months[$mon] $mday, $year at $time";



}



sub parse_form {



    # Define the configuration associative array.                            #

    %Config = ('recipient','',          'subject','',

               'email','',              'realname','',

               'redirect','',           'bgcolor','',

               'background','',         'link_color','',

               'vlink_color','',        'text_color','',

               'alink_color','',        'title','',

               'sort','',               'print_config','',

               'required','',           'env_report','',

               'return_link_title','',  'return_link_url','',

               'print_blank_fields','', 'missing_fields_redirect','');



    # Determine the form's REQUEST_METHOD (GET or POST) and split the form   #

    # fields up into their name-value pairs.  If the REQUEST_METHOD was      #

    # not GET or POST, send an error.                                        #

    if ($ENV{'REQUEST_METHOD'} eq 'GET') {

        # Split the name-value pairs

        @pairs = split(/&/, $ENV{'QUERY_STRING'});

    }

    elsif ($ENV{'REQUEST_METHOD'} eq 'POST') {

        # Get the input

        read(STDIN, $buffer, $ENV{'CONTENT_LENGTH'});

 

        # Split the name-value pairs

        @pairs = split(/&/, $buffer);

    }

    else {

        &error('request_method');

    }



    # For each name-value pair:                                              #

    foreach $pair (@pairs) {



        # Split the pair up into individual variables.                       #

        local($name, $value) = split(/=/, $pair);

 

        # Decode the form encoding on the name and value variables.          #

        # v1.92: remove null bytes                                           #

        $name =~ tr/+/ /;

        $name =~ s/%([a-fA-F0-9][a-fA-F0-9])/pack("C", hex($1))/eg;

        $name =~ tr/\0//d;



        $value =~ tr/+/ /;

        $value =~ s/%([a-fA-F0-9][a-fA-F0-9])/pack("C", hex($1))/eg;

        $value =~ tr/\0//d;



        # If the field name has been specified in the %Config array, it will #

        # return a 1 for defined($Config{$name}}) and we should associate    #

        # this value with the appropriate configuration variable.  If this   #

        # is not a configuration form field, put it into the associative     #

        # array %Form, appending the value with a ', ' if there is already a #

        # value present.  We also save the order of the form fields in the   #

        # @Field_Order array so we can use this order for the generic sort.  #

        if (defined($Config{$name})) {

            $Config{$name} = $value;

        }

        else {

            if ($Form{$name} ne '') {

                $Form{$name} = "$Form{$name}, $value";

            }

            else {

                push(@Field_Order,$name);

                $Form{$name} = $value;

            }

        }

    }



    # The next six lines remove any extra spaces or new lines from the       #

    # configuration variables, which may have been caused if your editor     #

    # wraps lines after a certain length or if you used spaces between field #

    # names or environment variables.                                        #

    $Config{'required'} =~ s/(\s+|\n)?,(\s+|\n)?/,/g;

    $Config{'required'} =~ s/(\s+)?\n+(\s+)?//g;

    $Config{'env_report'} =~ s/(\s+|\n)?,(\s+|\n)?/,/g;

    $Config{'env_report'} =~ s/(\s+)?\n+(\s+)?//g;

    $Config{'print_config'} =~ s/(\s+|\n)?,(\s+|\n)?/,/g;

    $Config{'print_config'} =~ s/(\s+)?\n+(\s+)?//g;



    # Split the configuration variables into individual field names.         #

    @Required = split(/,/,$Config{'required'});

    @Env_Report = split(/,/,$Config{'env_report'});

    @Print_Config = split(/,/,$Config{'print_config'});



    # ACCESS CONTROL FIX: Only allow ENV variables in @valid_ENV in          #

    # @Env_Report for security reasons.                                      #

    foreach $env_item (@Env_Report) {

        foreach $valid_item (@valid_ENV) {

            if ( $env_item eq $valid_item ) { push(@temp_array, $env_item) }

        }

    } 

    @Env_Report = @temp_array;

}



sub check_required {



    # Localize the variables used in this subroutine.                        #

    local($require, @error);



    # The following insures that there were no newlines in any fields which  #

    # will be used in the header.                                            #

    if ($Config{'subject'} =~ /(\n|\r)/m || $Config{'email'} =~ /(\n|\r)/m ||

        $Config{'realname'} =~ /(\n|\r)/m || $Config{'recipient'} =~ /(\n|\r)/m) {

        &error('invalid_headers');

    }



    if (!$Config{'recipient'}) {

        if (!defined(%Form)) { &error('bad_referer') }

        else                 { &error('no_recipient') }

    }

    else {

        # This block of code requires that the recipient address end with    #

        # a valid domain or e-mail address as defined in @recipients.        #

        $valid_recipient = 0;

        foreach $send_to (split(/,/,$Config{'recipient'})) {

            foreach $recipient (@recipients) {

                if ($send_to =~ /$recipient$/i) {

                    push(@send_to,$send_to); last;

                }

            }

        }

        if ($#send_to < 0) { &error('no_recipient') }

        $Config{'recipient'} = join(',',@send_to);

    }



    # For each require field defined in the form:                            #

    foreach $require (@Required) {



        # If the required field is the email field, the syntax of the email  #

        # address if checked to make sure it passes a valid syntax.          #

        if ($require eq 'email' && !&check_email($Config{$require})) {

            push(@error,$require);

        }



        # Otherwise, if the required field is a configuration field and it   #

        # has no value or has been filled in with a space, send an error.    #

        elsif (defined($Config{$require})) {

            if ($Config{$require} eq '') { push(@error,$require); }

        }



        # If it is a regular form field which has not been filled in or      #

        # filled in with a space, flag it as an error field.                 #

        elsif (!defined($Form{$require}) || $Form{$require} eq '') {

            push(@error,$require);

        }

    }



    # If any error fields have been found, send error message to the user.   #

    if (@error) { &error('missing_fields', @error) }

}



sub return_html {

    # Local variables used in this subroutine initialized.                   #

    local($key,$sort_order,$sorted_field);



    # Now that we have finished using form values for any e-mail related     #

    # reasons, we will convert all of the form fields and config values      #

    # to remove any cross-site scripting security holes.                     #

    local($field);

    foreach $field (keys %Config) {

        $safeConfig{$field} = &clean_html($Config{$field});

    }



    foreach $field (keys %Form) {

        $Form{$field} = &clean_html($Form{$field});

    }





    # If redirect option is used, print the redirectional location header.   #

    if ($Config{'redirect'}) {

        print "Location: $safeConfig{'redirect'}\n\n";

    }



    # Otherwise, begin printing the response page.                           #

    else {



        # Print HTTP header and opening HTML tags.                           #

        print "Content-type: text/html\n\n";

        print "<html>\n <head>\n";



        # Print out title of page                                            #

        if ($Config{'title'}) { print "<title>$safeConfig{'title'}</title>\n" }

        else                  { print "<title>Thank You</title>\n"        }



        print " </head>\n <body";



        # Get Body Tag Attributes                                            #

        &body_attributes;



        # Close Body Tag                                                     #

        print ">\n  <center>\n";



        # Print custom or generic title.                                     #

        if ($Config{'title'}) { print "<h1>$safeConfig{'title'}</h1>\n" }

        else { print "<h1>Thank You For Filling Out This Form</h1>\n" }



        print "</center>\n";



        print "Below is what you submitted to $safeConfig{'recipient'} on ";

        print "$date<p><hr size=1 width=75\%><p>\n";



        # If a sort order is specified, sort the form fields based on that.  #

        if ($Config{'sort'} =~ /^order:.*,.*/) {



            # Set the temporary $sort_order variable to the sorting order,   #

            # remove extraneous line breaks and spaces, remove the order:    #

            # directive and split the sort fields into an array.             #

            $sort_order = $Config{'sort'};

            $sort_order =~ s/(\s+|\n)?,(\s+|\n)?/,/g;

            $sort_order =~ s/(\s+)?\n+(\s+)?//g;

            $sort_order =~ s/order://;

            @sorted_fields = split(/,/, $sort_order);



            # For each sorted field, if it has a value or the print blank    #

            # fields option is turned on print the form field and value.     #

            foreach $sorted_field (@sorted_fields) {

                local $sfname = &clean_html($sorted_field);



                if ($Config{'print_blank_fields'} || $Form{$sorted_field} ne '') {

                    print "<b>$sfname:</b> $Form{$sorted_field}<p>\n";

                }

            }

        }



        # Otherwise, use the order the fields were sent, or alphabetic.      #

        else {



            # Sort alphabetically if requested.

            if ($Config{'sort'} eq 'alphabetic') {

                @Field_Order = sort @Field_Order;

            }



            # For each form field, if it has a value or the print blank      #

            # fields option is turned on print the form field and value.     #

            foreach $field (@Field_Order) {

                local $fname = &clean_html($field);



                if ($Config{'print_blank_fields'} || $Form{$field} ne '') {

                    print "<b>$fname:</b> $Form{$field}<p>\n";

                }

            }

        }



        print "<p><hr size=1 width=75%><p>\n";



        # Check for a Return Link and print one if found.                    #

        if ($Config{'return_link_url'} && $Config{'return_link_title'}) {

            print "<ul>\n";

            print "<li><a href=\"$safeConfig{'return_link_url'}\">$safeConfig{'return_link_title'}</a>\n";

            print "</ul>\n";

        }



        # Print the page footer.                                             #

        print <<"(END HTML FOOTER)";

        <hr size=1 width=75%><p> 

        <center><font size=-1><a href="http://www.scriptarchive.com/formmail.html">FormMail</a> V1.92 &copy; 1995 - 2002  Matt Wright<br>

A Free Product of <a href="http://www.scriptarchive.com/">Matt's Script Archive, Inc.</a></font></center>

        </body>

       </html>

(END HTML FOOTER)

    }

}



sub send_mail {

    # Localize variables used in this subroutine.                            #

    local($print_config,$key,$sort_order,$sorted_field,$env_report);



    # Open The Mail Program

    open(MAIL,"|$mailprog");



    print MAIL "To: $Config{'recipient'}\n";

    print MAIL "From: $Config{'email'} ($Config{'realname'})\n";



    # Check for Message Subject

    if ($Config{'subject'}) { print MAIL "Subject: $Config{'subject'}\n\n" }

    else                    { print MAIL "Subject: WWW Form Submission\n\n" }



    print MAIL "Below is the result of your feedback form.  It was submitted by\n";

    print MAIL "$Config{'realname'} ($Config{'email'}) on $date\n";

    print MAIL "-" x 75 . "\n\n";



    if (@Print_Config) {

        foreach $print_config (@Print_Config) {

            if ($Config{$print_config}) {

                print MAIL "$print_config: $Config{$print_config}\n\n";

            }

        }

    }



    # If a sort order is specified, sort the form fields based on that.      #

    if ($Config{'sort'} =~ /^order:.*,.*/) {



        # Remove extraneous line breaks and spaces, remove the order:        #

        # directive and split the sort fields into an array.                 #

        local $sort_order = $Config{'sort'};

        $sort_order =~ s/(\s+|\n)?,(\s+|\n)?/,/g;

        $sort_order =~ s/(\s+)?\n+(\s+)?//g;

        $sort_order =~ s/order://;

        @sorted_fields = split(/,/, $sort_order);



        # For each sorted field, if it has a value or the print blank        #

        # fields option is turned on print the form field and value.         #

        foreach $sorted_field (@sorted_fields) {

            if ($Config{'print_blank_fields'} || $Form{$sorted_field} ne '') {

                print MAIL "$sorted_field: $Form{$sorted_field}\n\n";

            }

        }

    }



    # Otherwise, print fields in order they were sent or alphabetically.     #

    else {



        # Sort alphabetically if specified:                                  #

        if ($Config{'sort'} eq 'alphabetic') {

            @Field_Order = sort @Field_Order;

        }



        # For each form field, if it has a value or the print blank          #

        # fields option is turned on print the form field and value.         #

        foreach $field (@Field_Order) {

            if ($Config{'print_blank_fields'} || $Form{$field} ne '') {

                print MAIL "$field: $Form{$field}\n\n";

            }

        }

    }



    print MAIL "-" x 75 . "\n\n";



    # Send any specified Environment Variables to recipient.                 #

    foreach $env_report (@Env_Report) {

        if ($ENV{$env_report}) {

            print MAIL "$env_report: $ENV{$env_report}\n";

        }

    }



    close (MAIL);

}



sub check_email {

    # Initialize local email variable with input to subroutine.              #

    $email = $_[0];



    # If the e-mail address contains:                                        #

    if ($email =~ /(@.*@)|(\.\.)|(@\.)|(\.@)|(^\.)/ ||



        # the e-mail address contains an invalid syntax.  Or, if the         #

        # syntax does not match the following regular expression pattern     #

        # it fails basic syntax verification.                                #



        $email !~ /^.+\@(\[?)[a-zA-Z0-9\-\.]+\.([a-zA-Z0-9]+)(\]?)$/) {



        # Basic syntax requires:  one or more characters before the @ sign,  #

        # followed by an optional '[', then any number of letters, numbers,  #

        # dashes or periods (valid domain/IP characters) ending in a period  #

        # and then 2 or 3 letters (for domain suffixes) or 1 to 3 numbers    #

        # (for IP addresses).  An ending bracket is also allowed as it is    #

        # valid syntax to have an email address like: user@[255.255.255.0]   #



        # Return a false value, since the e-mail address did not pass valid  #

        # syntax.                                                            #

        return 0;

    }



    else {



        # Return a true value, e-mail verification passed.                   #

        return 1;

    }

}



# This was added into v1.91 to further secure the recipients array.  Now, by #

# default it will assume that valid recipients include only users with       #

# usernames A-Z, a-z, 0-9, _ and - that match your domain exactly.  If this  #

# is not what you want, you should read more detailed instructions regarding #

# the configuration of the @recipients variable in the documentation.        #

sub fill_recipients {

    local(@domains) = @_;

    local($domain,@return_recips);



    foreach $domain (@domains) {

        if ($domain =~ /^\d+\.\d+\.\d+\.\d+$/) {

            $domain =~ s/\./\\\./g;

            push(@return_recips,'^[\w\-\.]+\@\[' . $domain . '\]');

        }

        else {

            $domain =~ s/\./\\\./g;

            $domain =~ s/\-/\\\-/g;

            push(@return_recips,'^[\w\-\.]+\@' . $domain);

        }

    }



    return @return_recips;

}



# This function will convert <, >, & and " to their HTML equivalents.        #

sub clean_html {

    local $value = $_[0];

    $value =~ s/\&/\&amp;/g;

    $value =~ s/</\&lt;/g;

    $value =~ s/>/\&gt;/g;

    $value =~ s/"/\&quot;/g;

    return $value;

}



sub body_attributes {

    # Check for Background Color

    if ($Config{'bgcolor'}) { print " bgcolor=\"$safeConfig{'bgcolor'}\"" }



    # Check for Background Image

    if ($Config{'background'}) { print " background=\"$safeConfig{'background'}\"" }



    # Check for Link Color

    if ($Config{'link_color'}) { print " link=\"$safeConfig{'link_color'}\"" }



    # Check for Visited Link Color

    if ($Config{'vlink_color'}) { print " vlink=\"$safeConfig{'vlink_color'}\"" }



    # Check for Active Link Color

    if ($Config{'alink_color'}) { print " alink=\"$safeConfig{'alink_color'}\"" }



    # Check for Body Text Color

    if ($Config{'text_color'}) { print " text=\"$safeConfig{'text_color'}\"" }

}



sub error { 

    # Localize variables and assign subroutine input.                        #

    local($error,@error_fields) = @_;

    local($host,$missing_field,$missing_field_list);



    if ($error eq 'bad_referer') {

        if ($ENV{'HTTP_REFERER'} =~ m|^https?://([\w\.]+)|i) {

            $host = $1;

            my $referer = &clean_html($ENV{'HTTP_REFERER'});

            print <<"(END ERROR HTML)";

Content-type: text/html



<html>

 <head>

  <title>Bad Referrer - Access Denied</title>

 </head>

 <body bgcolor=#FFFFFF text=#000000>

  <center>

   <table border=0 width=600 bgcolor=#9C9C9C>

    <tr><th><font size=+2>Bad Referrer - Access Denied</font></th></tr>

   </table>

   <table border=0 width=600 bgcolor=#CFCFCF>

    <tr><td>The form attempting to use

     <a href="http://www.scriptarchive.com/formmail.html">FormMail</a>

     resides at <tt>$referer</tt>, which is not allowed to access

     this cgi script.<p>



     If you are attempting to configure FormMail to run with this form, you need

     to add the following to \@referers, explained in detail in the 

     <a href="http://www.scriptarchive.com/readme/formmail.html">README</a> file.<p>



     Add <tt>'$host'</tt> to your <tt><b>\@referers</b></tt> array.<hr size=1>

     <center><font size=-1>

      <a href="http://www.scriptarchive.com/formmail.html">FormMail</a> V1.92 &copy; 1995 - 2002  Matt Wright<br>

      A Free Product of <a href="http://www.scriptarchive.com/">Matt's Script Archive, Inc.</a>

     </font></center>

    </td></tr>

   </table>

  </center>

 </body>

</html>

(END ERROR HTML)

        }

        else {

            print <<"(END ERROR HTML)";

Content-type: text/html



<html>

 <head>

  <title>FormMail v1.92</title>

 </head>

 <body bgcolor=#FFFFFF text=#000000>

  <center>

   <table border=0 width=600 bgcolor=#9C9C9C>

    <tr><th><font size=+2>FormMail</font></th></tr>

   </table>

   <table border=0 width=600 bgcolor=#CFCFCF>

    <tr><th><tt><font size=+1>Copyright 1995 - 2002 Matt Wright<br>

        Version 1.92 - Released April 21, 2002<br>

        A Free Product of <a href="http://www.scriptarchive.com/">Matt's Script Archive,

        Inc.</a></font></tt></th></tr>

   </table>

  </center>

 </body>

</html>

(END ERROR HTML)

        }

    }



    elsif ($error eq 'request_method') {

            print <<"(END ERROR HTML)";

Content-type: text/html



<html>

 <head>

  <title>Error: Request Method</title>

 </head>

 <body bgcolor=#FFFFFF text=#000000>

  <center>

   <table border=0 width=600 bgcolor=#9C9C9C>

    <tr><th><font size=+2>Error: Request Method</font></th></tr>

   </table>

   <table border=0 width=600 bgcolor=#CFCFCF>

    <tr><td>The Request Method of the Form you submitted did not match

     either <tt>GET</tt> or <tt>POST</tt>.  Please check the form and make sure the

     <tt>method=</tt> statement is in upper case and matches <tt>GET</tt> or <tt>POST</tt>.<p>



     <center><font size=-1>

      <a href="http://www.scriptarchive.com/formmail.html">FormMail</a> V1.92 &copy; 1995 - 2002  Matt Wright<br>

      A Free Product of <a href="http://www.scriptarchive.com/">Matt's Script Archive, Inc.</a>

     </font></center>

    </td></tr>

   </table>

  </center>

 </body>

</html>

(END ERROR HTML)

    }



    elsif ($error eq 'no_recipient') {

            print <<"(END ERROR HTML)";

Content-type: text/html



<html>

 <head>

  <title>Error: Bad/No Recipient</title>

 </head>

 <body bgcolor=#FFFFFF text=#000000>

  <center>

   <table border=0 width=600 bgcolor=#9C9C9C>

    <tr><th><font size=+2>Error: Bad/No Recipient</font></th></tr>

   </table>

   <table border=0 width=600 bgcolor=#CFCFCF>

    <tr><td>There was no recipient or an invalid recipient specified in the data sent to FormMail.  Please

     make sure you have filled in the <tt>recipient</tt> form field with an e-mail

     address that has been configured in <tt>\@recipients</tt>.  More information on filling in <tt>recipient</tt> form fields and variables can be

     found in the <a href="http://www.scriptarchive.com/readme/formmail.html">README</a> file.<hr size=1>



     <center><font size=-1>

      <a href="http://www.scriptarchive.com/formmail.html">FormMail</a> V1.92 &copy; 1995 - 2002  Matt Wright<br>

      A Free Product of <a href="http://www.scriptarchive.com/">Matt's Script Archive, Inc.</a>

     </font></center>

    </td></tr>

   </table>

  </center>

 </body>

</html>

(END ERROR HTML)

    }



    elsif ($error eq 'invalid_headers') {

            print <<"(END ERROR HTML)";

Content-type: text/html



<html>

 <head>

  <title>Error: Bad Header Fields</title>

 </head>

 <body bgcolor=#FFFFFF text=#000000>

  <center>

   <table border=0 width=600 bgcolor=#9C9C9C>

    <tr><th><font size=+2>Error: Bad Header Fields</font></th></tr>

   </table>

   <table border=0 width=600 bgcolor=#CFCFCF>

    <tr><td>The header fields, which include <tt>recipient</tt>, <tt>email</tt>, <tt>realname</tt> and <tt>subject</tt> were

     filled in with invalid values. You may not include any newline characters in these parameters.

     More information on filling in these form fields and variables can be

     found in the <a href="http://www.scriptarchive.com/readme/formmail.html">README</a> file.<hr size=1>



     <center><font size=-1>

      <a href="http://www.scriptarchive.com/formmail.html">FormMail</a> V1.92 &copy; 1995 - 2002  Matt Wright<br>

      A Free Product of <a href="http://www.scriptarchive.com/">Matt's Script Archive, Inc.</a>

     </font></center>

    </td></tr>

   </table>

  </center>

 </body>

</html>

(END ERROR HTML)

    }



    elsif ($error eq 'missing_fields') {

        if ($Config{'missing_fields_redirect'}) {

            print "Location: " . &clean_html($Config{'missing_fields_redirect'}) . "\n\n";

        }

        else {

            foreach $missing_field (@error_fields) {

                $missing_field_list .= "<li>" . &clean_html($missing_field) . "\n";

            }



            print <<"(END ERROR HTML)";

Content-type: text/html



<html>

 <head>

  <title>Error: Blank Fields</title>

 </head>

  <center>

   <table border=0 width=600 bgcolor=#9C9C9C>

    <tr><th><font size=+2>Error: Blank Fields</font></th></tr>

   </table>

   <table border=0 width=600 bgcolor=#CFCFCF>

    <tr><td>The following fields were left blank in your submission form:<p>

     <ul>

$missing_field_list

     </ul><br>



     These fields must be filled in before you can successfully submit the form.<p>

     Please use your browser's back button to return to the form and try again.<hr size=1>

     <center><font size=-1>

      <a href="http://www.scriptarchive.com/formmail.html">FormMail</a> V1.92 &copy; 1995 - 2002  Matt Wright<br>

      A Free Product of <a href="http://www.scriptarchive.com/">Matt's Script Archive, Inc.</a>

     </font></center>

    </td></tr>

   </table>

  </center>

 </body>

</html>

(END ERROR HTML)

        }

    }



    exit;

}






```

---

### Post by ju2wheels on 2009-03-09
There are plenty of things that can be going wrong so without more detail from you on what is going wrong I wont be much help.

One thing I did notice about your script is that it uses sendmail which is not configured by default on Ubuntu. In order to get sendmail working you must first install and configure exim.

---

### Post by Genesis427 on 2009-03-12
I am having some issues with perl and apache2.
Initially I started trying to get formmail.pl to run from a html form on our website.

Having no luck, I've been attempting to get test.pl and HelloWorld.pl (same code, different names).  
From [http://www.ourSite1/cgi-bin/anyfilename.pl](http://www.ourSite1/cgi-bin/anyfilename.pl),  and from /usr/lib/cgi-bin/anyfilename.pl, the browser wants to save the file or just shows the code.  It does not recognize the file as a script.  If I double click on either file, and choose run in terminal, the terminal opens but closes so quickly, I cannot see "Hello World!" if it is there.

I have tried several fixes suggested in other threads with no positive results. I believe that the .pl scripts are in ascii format and chmoded to 775 and +x. Both scripts have been created in gedit and/or from nano in the terminal.

There must be something that I have done wrong.
Any suggestions are welcome at this point.
Thank you.

We are running:
Ubuntu 8.04 (hardy)
Kernel Linux 2.6.24-23-server
Gnome 2.22.3
Apache2.2.8

Websites are in:
Filesystem
/var/www/ourSite1/
/var/www/ourSite2/

---

### Post by ju2wheels on 2009-03-12
1. I assume you have double checked your config against my comment above and it is the same.

2. Open /etc/apache2/mods-enabled/mime.conf and locate the following line:
```

AddHandler cgi-script .cgi

```

Then modify it to be this:

```

AddHandler cgi-script .cgi .pl

```

3. Make sure you have perl installed

4. Make sure the first line in your script is:
```

#!/usr/bin/perl

```

5. Make sure the .pl file owner/group are root:root

---

### Post by Genesis427 on 2009-03-12
ju2wheels,

thank you

I made the changes that you suggested.

I have installed and reinstalled perl several times now

From the terminal: "which" perl yields  /usr/bin/perl

I restarted apache2 from the terminal.

Browser still wants to save the file.

I re-read your first post here and found that I did not have a file called 000-default at /etc/apache2/sites-enabled/000-default.
I created one and saved it.
Now when restarting apache2 I get this:
"[Thu Mar 12 10:12:29 2009] [warn] The ScriptAlias directive in /etc/apache2/sites-enabled/000-default at line 1 will probably never match because it overlaps an earlier ScriptAlias."

Browser still wants to save the file.
Saved file is empty but the code is present when opened in the terminal via nano

---

### Post by Genesis427 on 2009-03-12
the cgi-bin directory in the /usr/lib/ had an emblem checked "unreadable",
I unchecked the emblem.

Still no change

---

### Post by ju2wheels on 2009-03-12
> **Genesis427 said:**
> 
I re-read your first post here and found that I did not have a file called 000-default at /etc/apache2/sites-enabled/000-default.


I wouldnt recommend creating that if its not already there as thats created by an automatic script using a2ensite and I was assuming the default apache configuration. It seems that your apache must be setup differently. I would remove it. If you had your two sites working in general before then their configuration has been appended to one of the other config files.

Would you mind posting your /etc/apache2/apache2.conf file which is most likely where you have all your config info (you can omit anything specifically identifying you like domain, email...).

---

### Post by ju2wheels on 2009-03-12
> **Genesis427 said:**
> the cgi-bin directory in the /usr/lib/ had an emblem checked "unreadable",
I unchecked the emblem.

Still no change

That might break your system, I would recommend you restore the permissions on that to what it was as that is a system directory.

---

### Post by Genesis427 on 2009-03-12
There was only one place at the end where I found any reference to our site.

#
# Based upon the NCSA server configuration files originally by Rob McCool.
#
# This is the main Apache server configuration file.  It contains the
# configuration directives that give the server its instructions.
# See [http://httpd.apache.org/docs/2.2/](http://httpd.apache.org/docs/2.2/) for detailed information about
# the directives.
#
# Do NOT simply read the instructions in here without understanding
# what they do.  They're here only as hints or reminders.  If you are unsure
# consult the online docs. You have been warned.  
#
# The configuration directives are grouped into three basic sections:
#  1. Directives that control the operation of the Apache server process as a
#     whole (the 'global environment').
#  2. Directives that define the parameters of the 'main' or 'default' server,
#     which responds to requests that aren't handled by a virtual host.
#     These directives also provide default values for the settings
#     of all virtual hosts.
#  3. Settings for virtual hosts, which allow Web requests to be sent to
#     different IP addresses or hostnames and have them handled by the
#     same Apache server process.
#
# Configuration and logfile names: If the filenames you specify for many
# of the server's control files begin with "/" (or "drive:/" for Win32), the
# server will use that explicit path.  If the filenames do *not* begin
# with "/", the value of ServerRoot is prepended -- so "/var/log/apache2/foo.log"
# with ServerRoot set to "" will be interpreted by the
# server as "//var/log/apache2/foo.log".
#

### Section 1: Global Environment
#
# The directives in this section affect the overall operation of Apache,
# such as the number of concurrent requests it can handle or where it
# can find its configuration files.
#

#
# ServerRoot: The top of the directory tree under which the server's
# configuration, error, and log files are kept.
#
# NOTE!  If you intend to place this on an NFS (or otherwise network)
# mounted filesystem then please read the LockFile documentation (available
# at <URL:http://httpd.apache.org/docs-2.1/mod/mpm_common.html#lockfile>);
# you will save yourself a lot of trouble.
#
# Do NOT add a slash at the end of the directory path.
#
ServerRoot "/etc/apache2"

#
# The accept serialization lock file MUST BE STORED ON A LOCAL DISK.
#
#<IfModule !mpm_winnt.c>
#<IfModule !mpm_netware.c>
LockFile /var/lock/apache2/accept.lock
#</IfModule>
#</IfModule>

#
# PidFile: The file in which the server should record its process
# identification number when it starts.
# This needs to be set in /etc/apache2/envvars
#
PidFile ${APACHE_PID_FILE}

#
# Timeout: The number of seconds before receives and sends time out.
#
Timeout 300

#
# KeepAlive: Whether or not to allow persistent connections (more than
# one request per connection). Set to "Off" to deactivate.
#
KeepAlive On

#
# MaxKeepAliveRequests: The maximum number of requests to allow
# during a persistent connection. Set to 0 to allow an unlimited amount.
# We recommend you leave this number high, for maximum performance.
#
MaxKeepAliveRequests 100

#
# KeepAliveTimeout: Number of seconds to wait for the next request from the
# same client on the same connection.
#
KeepAliveTimeout 15

##
## Server-Pool Size Regulation (MPM specific)
## 

# prefork MPM
# StartServers: number of server processes to start
# MinSpareServers: minimum number of server processes which are kept spare
# MaxSpareServers: maximum number of server processes which are kept spare
# MaxClients: maximum number of server processes allowed to start
# MaxRequestsPerChild: maximum number of requests a server process serves
<IfModule mpm_prefork_module>
    StartServers          5
    MinSpareServers       5
    MaxSpareServers      10
    MaxClients          150
    MaxRequestsPerChild   0
</IfModule>

# worker MPM
# StartServers: initial number of server processes to start
# MaxClients: maximum number of simultaneous client connections
# MinSpareThreads: minimum number of worker threads which are kept spare
# MaxSpareThreads: maximum number of worker threads which are kept spare
# ThreadsPerChild: constant number of worker threads in each server process
# MaxRequestsPerChild: maximum number of requests a server process serves
<IfModule mpm_worker_module>
    StartServers          2
    MaxClients          150
    MinSpareThreads      25
    MaxSpareThreads      75 
    ThreadsPerChild      25
    MaxRequestsPerChild   0
</IfModule>

# These need to be set in /etc/apache2/envvars
User www-data
Group www-data

#
# AccessFileName: The name of the file to look for in each directory
# for additional configuration directives.  See also the AllowOverride
# directive.
#

AccessFileName .htaccess

#
# The following lines prevent .htaccess and .htpasswd files from being 
# viewed by Web clients. 
#
<Files ~ "^\.ht">
    Order allow,deny
    Deny from all
</Files>

#
# DefaultType is the default MIME type the server will use for a document
# if it cannot otherwise determine one, such as from filename extensions.
# If your server contains mostly text or HTML documents, "text/plain" is
# a good value.  If most of your content is binary, such as applications
# or images, you may want to use "application/octet-stream" instead to
# keep browsers from trying to display binary files as though they are
# text.
#
DefaultType text/plain


#
# HostnameLookups: Log the names of clients or just their IP addresses
# e.g., [www.apache.org](www.apache.org) (on) or 204.62.129.132 (off).
# The default is off because it'd be overall better for the net if people
# had to knowingly turn this feature on, since enabling it means that
# each client request will result in AT LEAST one lookup request to the
# nameserver.
#
HostnameLookups Off

# ErrorLog: The location of the error log file.
# If you do not specify an ErrorLog directive within a <VirtualHost>
# container, error messages relating to that virtual host will be
# logged here.  If you *do* define an error logfile for a <VirtualHost>
# container, that host's errors will be logged there and not here.
#
ErrorLog /var/log/apache2/error.log

#
# LogLevel: Control the number of messages logged to the error_log.
# Possible values include: debug, info, notice, warn, error, crit,
# alert, emerg.
#
LogLevel warn

# Include module configuration:
Include /etc/apache2/mods-enabled/*.load
Include /etc/apache2/mods-enabled/*.conf

# Include all the user configurations:
Include /etc/apache2/httpd.conf

# Include ports listing
Include /etc/apache2/ports.conf

#
# The following directives define some format nicknames for use with
# a CustomLog directive (see below).
# If you are behind a reverse proxy, you might want to change %h into %{X-Forwarded-For}i
#
LogFormat "%h %l %u %t \"%r\" %>s %b \"%{Referer}i\" \"%{User-Agent}i\"" combined
LogFormat "%h %l %u %t \"%r\" %>s %b" common
LogFormat "%{Referer}i -> %U" referer
LogFormat "%{User-agent}i" agent

#
# ServerTokens
# This directive configures what you return as the Server HTTP response
# Header. The default is 'Full' which sends information about the OS-Type
# and compiled in modules.
# Set to one of:  Full | OS | Minor | Minimal | Major | Prod
# where Full conveys the most information, and Prod the least.
#
ServerTokens Full

#
# Optionally add a line containing the server version and virtual host
# name to server-generated pages (internal error documents, FTP directory 
# listings, mod_status and mod_info output etc., but not CGI generated 
# documents or custom error documents).
# Set to "EMail" to also include a mailto: link to the ServerAdmin.
# Set to one of:  On | Off | EMail
#
ServerSignature On



#
# Customizable error responses come in three flavors:
# 1) plain text 2) local redirects 3) external redirects
#
# Some examples:
#ErrorDocument 500 "The server made a boo boo."
#ErrorDocument 404 /missing.html
#ErrorDocument 404 "/cgi-bin/missing_handler.pl"
#ErrorDocument 402 [http://www.example.com/subscription_info.html](http://www.example.com/subscription_info.html)
#

#
# Putting this all together, we can internationalize error responses.
#
# We use Alias to redirect any /error/HTTP_<error>.html.var response to
# our collection of by-error message multi-language collections.  We use 
# includes to substitute the appropriate text.
#
# You can modify the messages' appearance without changing any of the
# default HTTP_<error>.html.var files by adding the line:
#
#   Alias /error/include/ "/your/include/path/"
#
# which allows you to create your own set of files by starting with the
# /usr/share/apache2/error/include/ files and copying them to /your/include/path/, 
# even on a per-VirtualHost basis.  The default include files will display
# your Apache version number and your ServerAdmin email address regardless
# of the setting of ServerSignature.
#
# The internationalized error documents require mod_alias, mod_include
# and mod_negotiation.  To activate them, uncomment the following 30 lines.

#    Alias /error/ "/usr/share/apache2/error/"
#
#    <Directory "/usr/share/apache2/error">
#        AllowOverride None
#        Options IncludesNoExec
#        AddOutputFilter Includes html
#        AddHandler type-map var
#        Order allow,deny
#        Allow from all
#        LanguagePriority en cs de es fr it nl sv pt-br ro
#        ForceLanguagePriority Prefer Fallback
#    </Directory>
#
#    ErrorDocument 400 /error/HTTP_BAD_REQUEST.html.var
#    ErrorDocument 401 /error/HTTP_UNAUTHORIZED.html.var
#    ErrorDocument 403 /error/HTTP_FORBIDDEN.html.var
#    ErrorDocument 404 /error/HTTP_NOT_FOUND.html.var
#    ErrorDocument 405 /error/HTTP_METHOD_NOT_ALLOWED.html.var
#    ErrorDocument 408 /error/HTTP_REQUEST_TIME_OUT.html.var
#    ErrorDocument 410 /error/HTTP_GONE.html.var
#    ErrorDocument 411 /error/HTTP_LENGTH_REQUIRED.html.var
#    ErrorDocument 412 /error/HTTP_PRECONDITION_FAILED.html.var
#    ErrorDocument 413 /error/HTTP_REQUEST_ENTITY_TOO_LARGE.html.var
#    ErrorDocument 414 /error/HTTP_REQUEST_URI_TOO_LARGE.html.var
#    ErrorDocument 415 /error/HTTP_UNSUPPORTED_MEDIA_TYPE.html.var
#    ErrorDocument 500 /error/HTTP_INTERNAL_SERVER_ERROR.html.var
#    ErrorDocument 501 /error/HTTP_NOT_IMPLEMENTED.html.var
#    ErrorDocument 502 /error/HTTP_BAD_GATEWAY.html.var
#    ErrorDocument 503 /error/HTTP_SERVICE_UNAVAILABLE.html.var
#    ErrorDocument 506 /error/HTTP_VARIANT_ALSO_VARIES.html.var



# Include of directories ignores editors' and dpkg's backup files,
# see README.Debian for details.

# Include generic snippets of statements
Include /etc/apache2/conf.d/

# Include the virtual host configurations:
Include /etc/apache2/sites-enabled/

ExtendedStatus On
<Location /server-status>
    SetHandler server-status
    Order deny,allow
    Deny from all
    Allow from 127.0.0.1
</Location>


<Directory /var/www/ourSite1/cgi-bin/>
Options ExecCGI
</Directory>

---

### Post by ju2wheels on 2009-03-12
Do you have any other files in /etc/apache2/sites-enabled as I dont see the prior Script Alias its referring to? Also you can place the text you paste in between code tags (in the advanced editor use the "#" icon at the top) so it shows up in a box.

---

### Post by Genesis427 on 2009-03-12
removed the 000-default file

the permissions on the cgi-bin directory are reset
Edit/preferences of the cgi-bin - "Run executable test files when they are opened" radio button was not selected

restarted server again

browser still wants to save file

---

### Post by Genesis427 on 2009-03-12
there are two files in the sites enabled file named for oursite1 and oursite2

---

### Post by ju2wheels on 2009-03-12
Ok then those are the files Ill need to see as they define how your websites are configured.

---

### Post by Genesis427 on 2009-03-12
Here the two sites enabled:

OurSite1:

#
#  OurSite1.com
#
<VirtualHost *>
        ServerAdmin [email]webmaster@OurSite1.com[/email]
        ServerName  [www.OurSite1.com](www.OurSite1.com)
        ServerAlias OurSite1.com

        # Indexes + Directory Root.
        DirectoryIndex index.htm
        DocumentRoot /var/www/OurSite1

        # CGI Directory
        ScriptAlias /cgi-bin/ var/www/OurSite1/cgi-bin/
        <Location /cgi-bin>
                Options +ExecCGI
        </Location>

Site Number Two:
#
#  OurSite2.com
#
<VirtualHost *>
        ServerAdmin [email]webmaster@OurSite2.com[/email]
        ServerName  [www.OurSite2.com](www.OurSite2.com)
        ServerAlias OurSite2.com

        # Indexes + Directory Root.
        DirectoryIndex index.htm
        DocumentRoot /var/www/OurSite2

        # CGI Directory
        ScriptAlias /cgi-bin/ var/www/OurSite2/cgi-bin/
        <Location /cgi-bin>
                Options +ExecCGI
        </Location>

---

### Post by Genesis427 on 2009-03-12
Hellow World worked.

With my html form action set to:[http://www.OurSite1.com/formmail.pl](http://www.OurSite1.com/formmail.pl)
when the form is submitted, we get the Internal Server Error message
the bottom line is:
Apache 2.2.8 (Ubuntu)mod_perl/2.0.3 Perl/v5.8.8 Server at [www.OurSite1.com](www.OurSite1.com) Port 80

With my html form action set to: [http://www.OUrSite1.com/cgi-bin/formmail.pl](http://www.OUrSite1.com/cgi-bin/formmail.pl)
when the form is submitted, we get the fire not found screen

---

### Post by ju2wheels on 2009-03-12
I think what you want is the following (whether you use two separate files or place them both in one file in sites-enabled folder should not matter):

Site One:
```

<VirtualHost *>
ServerAdmin webmaster@OurSite1.com
ServerName www.OurSite1.com
ServerAlias OurSite1.com
	
	DocumentRoot /var/www/OurSite1/
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/OurSite1/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
	</Directory>

	<Directory /var/www/OurSite1/cgi-bin/>
		AllowOverride None
		Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
		Order allow,deny
		Allow from all
	</Directory>

	ErrorLog /var/log/apache2/error_site1.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog /var/log/apache2/access_site1.log combined
	ServerSignature Off

</VirtualHost>

```

Site 2:
```

<VirtualHost *>
ServerAdmin webmaster@OurSite2.com
ServerName www.OurSite2.com
ServerAlias OurSite2.com
	
	DocumentRoot /var/www/OurSite2/
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/OurSite2/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
	</Directory>

	<Directory /var/www/OurSite2/cgi-bin/>
		AllowOverride None
		Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
		Order allow,deny
		Allow from all
	</Directory>

	ErrorLog /var/log/apache2/error_site2.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog /var/log/apache2/access_site2.log combined
	ServerSignature Off

</VirtualHost>

```

You will thus now have to actually create the folders /var/www/Oursite1/cgi-bin/ and /var/www/Oursite2/cgi-bin/ and place your cgi scripts in their respective folders.

You have to also remove the following from the end of /etc/apache2/apache2.conf:
```

<Directory /var/www/ourSite1/cgi-bin/>
Options ExecCGI
</Directory>

```

The directory index should already include htm/html and it is actually set in  /etc/apache2/mods-enabled/dir.conf 

Hope that helps...

---

### Post by Genesis427 on 2009-03-12
ju2wheels, thank you

I made the changes you suggested and
Hello World worked. ([http://www.oursite1.com/test.pl](http://www.oursite1.com/test.pl))

With my html form action set to:[http://www.OurSite1.com/formmail.pl](http://www.OurSite1.com/formmail.pl)
when the form is submitted, we get the Internal Server Error message
the bottom line is:
Apache 2.2.8 (Ubuntu)mod_perl/2.0.3 Perl/v5.8.8 Server at [www.OurSite1.com](www.OurSite1.com) Port 80

With my html form action set to: [http://www.OurSite1.com/cgi-bin/formmail.pl](http://www.OurSite1.com/cgi-bin/formmail.pl)
when the form is submitted, we get the file not found screen

do you have any more suggestions?

once again, thank you for your help and your patience

edit: added: /var/log/messages "Mar 12 15:26:12 webserver -- MARK --"

---

### Post by ju2wheels on 2009-03-12
What folder did you place formmail.pl in? Both test.pl and formmail.pl should be in /var/www/Oursite1/cgi-bin/.

Example:

A file /var/www/Oursite1/test.html can have a form:

```

....

<form action="cgi-bin/formmail.pl">
....
</form>
......

```

Then that invokes the cgi file /var/www/Oursite/cgi-bin/formmail.pl which should process the input and print an HTML page in return.

---

### Post by Genesis427 on 2009-03-12
progress 
now with the form action set to :[http://www.oursite1.com/cgi-bin/formmail.pl](http://www.oursite1.com/cgi-bin/formmail.pl), we get the Internal Server Error screen.

That should indicate that there is an issue within my formmail script, correct?

here is the beginning of the formmail script:

```
#!/usr/bin/perl -wT

#

# NMS FormMail Version 3.14c1

#



use strict;

use vars qw(

  $DEBUGGING $emulate_matts_code $secure %more_config

  $allow_empty_ref $max_recipients $mailprog @referers

  @allow_mail_to @recipients %recipient_alias

  @valid_ENV $date_fmt $style $send_confirmation_mail

  $confirmation_text $locale $charset $no_content

  $double_spacing $wrap_text $wrap_style $postmaster 

  $address_style

);



# PROGRAM INFORMATION

# -------------------

# FormMail.pl Version 3.14c1

#

# This program is licensed in the same way as Perl

# itself. You are free to choose between the GNU Public

# License <http://www.gnu.org/licenses/gpl.html>  or

# the Artistic License

# <http://www.perl.com/pub/a/language/misc/Artistic.html>

#

# For help on configuration or installation see the

# README file or the POD documentation at the end of

# this file.



# USER CONFIGURATION SECTION

# --------------------------

# Modify these to your own settings. You might have to

# contact your system administrator if you do not run

# your own web server. If the purpose of these

# parameters seems unclear, please see the README file.

#

BEGIN

{

  $DEBUGGING         = 1;

  $emulate_matts_code= 0;

  $secure            = 1;

  $allow_empty_ref   = 1;

  $max_recipients    = 5;

  $mailprog          = '/usr/sbin/sendmail -t';

  $postmaster        = '';

  @referers          = qw(www.oursite1.com);

  @allow_mail_to     = qw(info@oursite1.com);

  @recipients        = ();

  %recipient_alias   = ();

  @valid_ENV         = qw(REMOTE_HOST REMOTE_ADDR REMOTE_USER HTTP_USER_AGENT);

  $locale            = '';

  $charset           = 'iso-8859-1';

  $date_fmt          = '%A, %B %d, %Y at %H:%M:%S';

  $style             = '/css/nms.css';

  $no_content        = 0;

  $double_spacing    = 1;

  $wrap_text         = 0;

  $wrap_style        = 1;

  $address_style     = 0;

  $send_confirmation_mail = 0;

  $confirmation_text = <<'END_OF_CONFIRMATION';

From: info@oursite1.com

Subject: form submission



Thank you for your form submission.



END_OF_CONFIRMATION



# You may need to uncomment the line below and adjust the path.

# use lib './lib';
```

---

### Post by ju2wheels on 2009-03-12
Yes most likely. As I stated in one of the previous posts, sendmail is not setup correctly by default on Ubuntu and you have to install and configure exim for it to work.

If a simple test file like /var/www/Oursite1/cgi-bin/test.pl containing this:
```

#!/usr/bin/perl -wT

print "<html><head><title>Test</title></head><body><h1>It Works</h1></body></html>";

```

If that works when you visit [http://oursite1.com/cgi-bin/test.pl](http://oursite1.com/cgi-bin/test.pl) and you see "It works" in the browser then you are done configuring cgi and its working properly and any errors now are a result of your code.

---

### Post by Genesis427 on 2009-03-12
ju2wheels,

thank you for your help

test.pl coded as one would the helloworld.pl script works from [http://www/oursite1.com/cgi-bin/test.pl](http://www/oursite1.com/cgi-bin/test.pl)

So, tomorrow, I will install and configure exim

Once again, thank you

---

### Post by Genesis427 on 2009-03-13
I have installed and configured exim4.
Likely I have configured it improperly.

When submitting the form the Internal Server Error is:
```
close sendmail pipe failed, mail prog=(/usr/sbin/exim4 -t) at (eval 8) line 216
```

---

### Post by Genesis427 on 2009-03-13
I changed:
```
$mailprog          = '/usr/sbin/exim4 -t'; to $mailprog          = '/usr/sbin/exim4 t- i-';
```
and my thanks page came up in the browser.

No email was sent, so I still have something to repair.

---

### Post by ju2wheels on 2009-03-13
You dont need to use exim directly like that as the syntax is most likely different. The benefit to using exim is that it creates a symbolic link and pretends to be the old school sendmail. So the original mailprog command should work once you have exim configured properly. You can test if its setup properly by googling for command line sendmail for instructions on how to send an email from the command line and test it by sending an email to yourself manually.

So I would try $mailprog = '/usr/sbin/sendmail -t -i'.

A second thing to be aware of, is depending on your firewall (if you are in a corporate setting or potentially even your web host), you may need to use an authenticated SMTP in order for mail to reach people outside of the network your server is on.

---

### Post by Genesis427 on 2009-03-13
ju2wheels,

thank you

I will make the changes and give it a test soon

---

### Post by Genesis427 on 2009-03-16
I've tried to reconfigure exim4, reinstalled it several times (apparently improperly) and this is what I get when attempting to reconfigure:
```
exim4-config is broken or not fully installed
```

---

### Post by Genesis427 on 2009-03-16
Package `exim-config' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: exim-config is not installed
webserver@webserver:~$ sudo dpkg-reconfigure exim4-config
/usr/sbin/dpkg-reconfigure: exim4-config is broken or not fully installed
webserver@webserver:~$ sudo apt-get install exim4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  exim4: Depends: exim4-base (>= 4.69) but it is not going to be installed
  exim4-daemon-light: Depends: exim4-base (>= 4.69) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
webserver@webserver:~$ sudo apt-get -f install exim4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  exim4: Depends: exim4-base (>= 4.69) but it is not going to be installed
  exim4-daemon-light: Depends: exim4-base (>= 4.69) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

---

### Post by Genesis427 on 2009-03-17
purged and reinstalled exim4

set up smpt authentication (TLS) and saslauthd.
Configured SASL as descriped at: 
[https://help.ubuntu.com/8.04/serverguide/C/exim4.html](https://help.ubuntu.com/8.04/serverguide/C/exim4.html)

I can send email from this server via Evolution Mail, but not via the formmail script and sendmail/exim4

still working it

---

### Post by ju2wheels on 2009-03-17
When you say that you can send mail from the server through Evolution do you mean configured Evolution to send mail using the localhost as the mail server or did you configure it manage your mail for another email service (gmail, yahoo, hotmail etc).

When I configured exim on my machine I only had to do what was in the configuration section on the page you linked. After I did that I add the SMTP credentials to /etc/exim4/passwd.client. If you edit that file you add a line like this to it:

```

mail.server.com:user_name:password

```

Then exim will use that to authenticate to the mail server.

If you setup the MTA then I would first check to see if sendmail is working by sending an email from the command line using sendmail directly and not Evolution (send an email to an email address that is not on the same domain as your server).

[http://www.kangry.com/topics/viewcomment.php?index=427](http://www.kangry.com/topics/viewcomment.php?index=427)

---

### Post by Genesis427 on 2009-03-17
yes, I can send email using Evolution Mail connecting to OurEmailHost via smtp.ourdomain.com

I was able to send an email to another domain via the terminal.

edited the file /etc/exim4/passwd.client:

```
mail.ourDomain.com:webmaster@ourDomain.com:OurPassword

```

My brain hurts - this should work

---

### Post by Genesis427 on 2009-03-17
All I set out to do was:
collect data from an html form on our website, and send it as an email to one of our email accounts - sent from our webserver (Ubuntu/Apache2)

My understanding is that to do this one:
downloads perl
downloads and configures formmail.pl
downloads sendmail
downloads and configures exim4

Was there a better way to do this?

---

### Post by ju2wheels on 2009-03-17
If you were able to send an email from the command line then your exim and sendmail are setup correctly and you shouldnt need to add the SMTP user to the /etc/exim4/passwd.client and I recommend you dont or else it will always use this.

In order to do what you want the order is this:

1. Download/install/config: apache, cgi, perl, exim4 (aka sendmail) 
2. You write a cgi script that takes as input the values of the fields in your submission form. This is then piped into the command "/usr/bin/sendmail -t -i " + parameters and email info which then uses the servers local exim setup (the MTA in specific) to send out the email. This is what the formmail.pl does for you if you are referring to this one: [http://www.scriptarchive.com/formmail.html](http://www.scriptarchive.com/formmail.html) .

Using the above script set $mailprog = '/usr/sbin/sendmail -t -i' and I believe that should be the only change needed although I havent tried it myself.

---

### Post by Genesis427 on 2009-03-18
At the top in the user configuration section,'/usr/sbin/sendmail -t -i' is what I entered into the script at mailprog=.

This morning I started with a clean copy of the script and made the changes you suggested.  (basically changed lib to sbin and (-oi -t) to (-t -i) in the mailprog= line).

The following code is present in the formmail script in several places in areas not to be edited by the user ```
'/usr/lib/sendmail -oi -t',
```
However, I have not altered it in those places.

This morning, I could not send email from the terminal (but was able to before the edits to passwd.client), so, I removed the line added in /etc/exim4/passwd.client, and now I can send email from the terminal.

The formmail script runs, redirects to my thank you html page, but I receive no email.  I must have something set wrong somewhere.

Thank you for your good advise on this adventure.

---

### Post by ju2wheels on 2009-03-18
I looked over the script again, I forgot to mention you will also have to edit this line at the top of the script as well:

```

@referers = ('scriptarchive.com','209.196.21.3');

```

It should be:

```

@referers = ('your_domain.com','SERVER_IP');

```

---

### Post by Genesis427 on 2009-03-18
I made the changes to the referers: line

Then when submitting the form in the browser I get the following error message screen:
```
close sendmail pipe failed, mailprog=[/usr/sbin/sendmail -t -i] at (eval 8) line 108
```

It was taking me to the thankyou.html page but now we have an error.

---

### Post by ju2wheels on 2009-03-18
Are you using a custom script other than the one linked above? Could you link me to it if its available online. I looked at the formmail script that I linked above and it doesnt have anything on line 108 that attempts to close an open mail pipe so I can keep suggesting things but Id rather be looking at what you are working with if possible so I dont send you running in circles.

One other thing to note is that if your script has a recipient section like the one i linked to above and the email address that is receiving these emails is not an @yourdomain.com address then you will need to modify the recipient field.

---

### Post by Genesis427 on 2009-03-18
ju2wheels,

thank you for all of your help

I have decided to take the form off of our website and forget all about formmail, sendmail and exim4.

I'm sure I must have set up something incorrectly.

Thanks again for all of your help.

---

### Post by Genesis427 on 2009-06-18
I revisited the web form adventure and this time I prevailed.

I had to reinstall Ubuntu, apache2, etc. for another reason and decided to give the web form email another try.

Followed ju2wheels' instructions and eventually configured exim4 properly.
The form works and the emails are sent.

Thank you ju2wheels for all of your help and patience.

Genesis427

---


---
title: "CheckGmail - Non XML standard Label names Patch"
date: 2009-06-16
forum: General Help
---

### Post by JFire on 2009-06-16
Heyas,

[https://sourceforge.net/forum/forum.php?thread_id=3305070&forum_id=463625](https://sourceforge.net/forum/forum.php?thread_id=3305070&forum_id=463625)

Describes a patch to get CheckGmail working with non-XML conforming Label names. (ie. Labels that include non standard characters such as spaces(!?), brackets and email characters.

Instructions:

1. open checkgmail for editing in your favourite editor (in Ubuntu Jaunty it's located at /usr/bin/checkgmail) 
 
2. paste the following function somewhere around line 1421, in between "sub write_prefs { ... }" and "sub convert_labels_from_hash { ...}" 
 

```
# XML has some very strict rules about naming conventions for keynames. Most special characters including spaces and commas are not allowed. 
# However, Gmail seems to allow their label names to be named almost anything. It seems that only the ^ character isn't allowed. 
# On June 16th 2009, the following was a valid Gmail label: !@#$%&*()-+}{\|'";:/?.>,<=~`  
# So, in an effort to make CheckGmail compatible with lables that include spaces, commas and other strange characters (such as @), I've put together this dirty hack. 
# I'm sure that hardly anyone will choose most of the included special characters for their labels ... but here it is anyway. 
# June 17th, 2009 - Goran Seletkovic 
 
sub XML_Buffer { 
my %subs = (_xSPACE_=>" ",_xEMAIL_=>"@",_xLBRACE_=>'\[',_xRBRACE_=>'\]',_xEXCLAIM_=>"!",_xHASH_=>"#",_xDOLLAR_=>"\\\$",_xPERCENTAGE_=>"%",_xAND_=>"&",_xMULTIPLY_=>"\\*",_xLBRACKET_=>"\\(",_xRBRACKET_=>"\\)",_xMINUS_=>"-",_xPLUS_=>"\\+",_xRCURLYBRAK_=>"}",_xLCURLYBRAK_=>"{",_xBACKSLASH_=>"\\\\",_xPIPE_=>"\\|",_xSINGLEQUOTE_=>"'",_xDOUBLEQUOTE_=>'"',_xSEMICOLON_=>";",_xCOLON_=>":",_xSLASH_=>"/",_xQUESTION_=>"\\?",_xDOT_=>"\\.",_xGREATERTHAN_=>"\\>",_xLESSTHAN_=>"\\<",_xCOMMA_=>",",_xEQUALS=>"=",_xTILDE_=>"~",_xAPOSTROPHY_=>"`"); 
my $k; my %temp = %label_delay;  
%label_delay=(); 
 
foreach my $j (keys(%temp)) { 
$k = $j; 
foreach (keys %subs) { 
if ((caller(1))[3] =~ /from_array/) {$j =~ s/$subs{$_}/$_/g;} #Perform the XML hack. Convert special characters in keynames to something the XML_parser can handle. 
if ((caller(1))[3] =~ /from_hash/) {$subs{$_} =~ s/\\([\$|\*|\(|\)|\+|\\|\||\?|\.|\>|\<])/$1/g ;$j =~ s/$_/$subs{$_}/g;} #Reverse the XML hack. 
} 
$label_delay{$j} = $temp{$k}; #rebuild the Hash 
}; 
} 

```

3. Add two calls to XML_Buffer. One in the "convert_labels_from_array" function and the other in the "convert_labels_from_hash" function. 
 
```

sub convert_labels_from_hash { 
XML_Buffer(); 
@labels=();  
push @labels, {label => "$_", delay => $label_delay{$_}} 
foreach sort(keys(%label_delay)); 
} 
 
sub convert_labels_from_array { 
%label_delay=(); 
$label_delay{$_->{label}} = $_->{delay} foreach @labels; 
XML_Buffer(); 
} 

``` 
 
 
Enjoy :-) 
 
~ G

---


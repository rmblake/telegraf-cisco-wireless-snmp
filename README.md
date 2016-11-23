# telegraf-cisco-wireless-snmp
Example config to pull down Cisco Wireless Controller/AP stats into telegraf by SNMP

Tested with Telegraf 1.1.0 (Will not work in earlier versions as the SNMP plugin does not support `oid_index_suffix`

## How to use
Make sure you've installed Cisco MIBs into a folder which is readable by snmptranslate (or define the mibdirs variable as descriped in the SNMP plugin docs at https://github.com/influxdata/telegraf/tree/master/plugins/inputs/snmp )

Copy the config file to telegraf.d/ in your telegraf config dir (which is `/etc/telegraf` under Ubuntu, at least).

Define your WLCs and SNMP communities in the config file - make sure you have outputs defined in telegraf, and data should start to be collected

## Caveats
You probably want at least 20 seconds between collection attempts, as SNMP isn't the fastest.

I'd rather be doing this with NETCONF and YANG which slowly seems to be making its way into IOS-XE, but it's not available in the AirOS code - hopefully this will change soon. 

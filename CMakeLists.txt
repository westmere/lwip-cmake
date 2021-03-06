option(USE_STATIC_LWIP_LIBRARY "Build lwip static library." ON)
option(USE_OBJECT_LWIP_LIBRARY "Build lwip object library." OFF)

set(LWIPDIR lwip/src)

# COREFILES, CORE4FILES: The minimum set of files needed for lwIP.
set(COREFILES ${LWIPDIR}/core/init.c
	${LWIPDIR}/core/def.c
	${LWIPDIR}/core/dns.c
	${LWIPDIR}/core/inet_chksum.c
	${LWIPDIR}/core/ip.c
	${LWIPDIR}/core/mem.c
	${LWIPDIR}/core/memp.c
	${LWIPDIR}/core/netif.c
	${LWIPDIR}/core/pbuf.c
	${LWIPDIR}/core/raw.c
	${LWIPDIR}/core/stats.c
	${LWIPDIR}/core/sys.c
	${LWIPDIR}/core/altcp.c
	${LWIPDIR}/core/altcp_alloc.c
	${LWIPDIR}/core/altcp_tcp.c
	${LWIPDIR}/core/tcp.c
	${LWIPDIR}/core/tcp_in.c
	${LWIPDIR}/core/tcp_out.c
	${LWIPDIR}/core/timeouts.c
	${LWIPDIR}/core/udp.c
)

set(CORE4FILES ${LWIPDIR}/core/ipv4/autoip.c
	${LWIPDIR}/core/ipv4/dhcp.c
	${LWIPDIR}/core/ipv4/etharp.c
	${LWIPDIR}/core/ipv4/icmp.c
	${LWIPDIR}/core/ipv4/igmp.c
	${LWIPDIR}/core/ipv4/ip4_frag.c
	${LWIPDIR}/core/ipv4/ip4.c
	${LWIPDIR}/core/ipv4/ip4_addr.c
)
	
set(CORE6FILES ${LWIPDIR}/core/ipv6/dhcp6.c
	${LWIPDIR}/core/ipv6/ethip6.c
	${LWIPDIR}/core/ipv6/icmp6.c
	${LWIPDIR}/core/ipv6/inet6.c
	${LWIPDIR}/core/ipv6/ip6.c
	${LWIPDIR}/core/ipv6/ip6_addr.c
	${LWIPDIR}/core/ipv6/ip6_frag.c
	${LWIPDIR}/core/ipv6/mld6.c
	${LWIPDIR}/core/ipv6/nd6.c
)

# APIFILES: The files which implement the sequential and socket APIs.
set(APIFILES ${LWIPDIR}/api/api_lib.c
	${LWIPDIR}/api/api_msg.c
	${LWIPDIR}/api/err.c
	${LWIPDIR}/api/if_api.c
	${LWIPDIR}/api/netbuf.c
	${LWIPDIR}/api/netdb.c
	${LWIPDIR}/api/netifapi.c
	${LWIPDIR}/api/sockets.c
	${LWIPDIR}/api/tcpip.c
)

# NETIFFILES: Files implementing various generic network interface functions
set(NETIFFILES ${LWIPDIR}/netif/ethernet.c
	${LWIPDIR}/netif/bridgeif.c
	${LWIPDIR}/netif/bridgeif_fdb.c
	${LWIPDIR}/netif/slipif.c
)

# SIXLOWPAN: 6LoWPAN
set(SIXLOWPAN ${LWIPDIR}/netif/lowpan6.c
	${LWIPDIR}/netif/lowpan6_ble.c
	${LWIPDIR}/netif/zepif.c
)

# PPPFILES: PPP
set(PPPFILES ${LWIPDIR}/netif/ppp/auth.c
	${LWIPDIR}/netif/ppp/ccp.c
	${LWIPDIR}/netif/ppp/chap-md5.c
	${LWIPDIR}/netif/ppp/chap_ms.c
	${LWIPDIR}/netif/ppp/chap-new.c
	${LWIPDIR}/netif/ppp/demand.c
	${LWIPDIR}/netif/ppp/eap.c
	${LWIPDIR}/netif/ppp/ecp.c
	${LWIPDIR}/netif/ppp/eui64.c
	${LWIPDIR}/netif/ppp/fsm.c
	${LWIPDIR}/netif/ppp/ipcp.c
	${LWIPDIR}/netif/ppp/ipv6cp.c
	${LWIPDIR}/netif/ppp/lcp.c
	${LWIPDIR}/netif/ppp/magic.c
	${LWIPDIR}/netif/ppp/mppe.c
	${LWIPDIR}/netif/ppp/multilink.c
	${LWIPDIR}/netif/ppp/ppp.c
	${LWIPDIR}/netif/ppp/pppapi.c
	${LWIPDIR}/netif/ppp/pppcrypt.c
	${LWIPDIR}/netif/ppp/pppoe.c
	${LWIPDIR}/netif/ppp/pppol2tp.c
	${LWIPDIR}/netif/ppp/pppos.c
	${LWIPDIR}/netif/ppp/upap.c
	${LWIPDIR}/netif/ppp/utils.c
	${LWIPDIR}/netif/ppp/vj.c
	${LWIPDIR}/netif/ppp/polarssl/arc4.c
	${LWIPDIR}/netif/ppp/polarssl/des.c
	${LWIPDIR}/netif/ppp/polarssl/md4.c
	${LWIPDIR}/netif/ppp/polarssl/md5.c
	${LWIPDIR}/netif/ppp/polarssl/sha1.c
)

# LWIPNOAPPSFILES: All LWIP files without apps
set(LWIPNOAPPSFILES ${COREFILES}
	${CORE4FILES}
	${CORE6FILES}
	${APIFILES}
	${NETIFFILES}
	${PPPFILES}
	${SIXLOWPAN}
)

# SNMPFILES: SNMPv2c agent
set(SNMPFILES ${LWIPDIR}/apps/snmp/snmp_asn1.c
	${LWIPDIR}/apps/snmp/snmp_core.c
	${LWIPDIR}/apps/snmp/snmp_mib2.c
	${LWIPDIR}/apps/snmp/snmp_mib2_icmp.c
	${LWIPDIR}/apps/snmp/snmp_mib2_interfaces.c
	${LWIPDIR}/apps/snmp/snmp_mib2_ip.c
	${LWIPDIR}/apps/snmp/snmp_mib2_snmp.c
	${LWIPDIR}/apps/snmp/snmp_mib2_system.c
	${LWIPDIR}/apps/snmp/snmp_mib2_tcp.c
	${LWIPDIR}/apps/snmp/snmp_mib2_udp.c
	${LWIPDIR}/apps/snmp/snmp_snmpv2_framework.c
	${LWIPDIR}/apps/snmp/snmp_snmpv2_usm.c
	${LWIPDIR}/apps/snmp/snmp_msg.c
	${LWIPDIR}/apps/snmp/snmpv3.c
	${LWIPDIR}/apps/snmp/snmp_netconn.c
	${LWIPDIR}/apps/snmp/snmp_pbuf_stream.c
	${LWIPDIR}/apps/snmp/snmp_raw.c
	${LWIPDIR}/apps/snmp/snmp_scalar.c
	${LWIPDIR}/apps/snmp/snmp_table.c
	${LWIPDIR}/apps/snmp/snmp_threadsync.c
	${LWIPDIR}/apps/snmp/snmp_traps.c
)

# HTTPFILES: HTTP server + client
set(HTTPFILES ${LWIPDIR}/apps/http/altcp_proxyconnect.c
	${LWIPDIR}/apps/http/fs.c
	${LWIPDIR}/apps/http/http_client.c
	${LWIPDIR}/apps/http/httpd.c
)

# MAKEFSDATA: MAKEFSDATA HTTP server host utility
set(MAKEFSDATAFILES ${LWIPDIR}/apps/http/makefsdata/makefsdata.c)

# LWIPERFFILES: IPERF server
set(LWIPERFFILES ${LWIPDIR}/apps/lwiperf/lwiperf.c)

# SMTPFILES: SMTP client
set(SMTPFILES ${LWIPDIR}/apps/smtp/smtp.c)

# SNTPFILES: SNTP client
set(SNTPFILES ${LWIPDIR}/apps/sntp/sntp.c)

# MDNSFILES: MDNS responder
set(MDNSFILES ${LWIPDIR}/apps/mdns/mdns.c)

# NETBIOSNSFILES: NetBIOS name server
set(NETBIOSNSFILES ${LWIPDIR}/apps/netbiosns/netbiosns.c)

# TFTPFILES: TFTP server files
set(TFTPFILES ${LWIPDIR}/apps/tftp/tftp_server.c)

# MQTTFILES: MQTT client files
set(MQTTFILES ${LWIPDIR}/apps/mqtt/mqtt.c)

# MBEDTLS_FILES: MBEDTLS related files of lwIP rep
set(MBEDTLS_FILES ${LWIPDIR}/apps/altcp_tls/altcp_tls_mbedtls.c
	${LWIPDIR}/apps/altcp_tls/altcp_tls_mbedtls_mem.c
	${LWIPDIR}/apps/snmp/snmpv3_mbedtls.c
)

# LWIPAPPFILES: All LWIP APPs
set(LWIPAPPFILES ${SNMPFILES}
	${HTTPFILES}
	${LWIPERFFILES}
	${SMTPFILES}
	${SNTPFILES}
	${MDNSFILES}
	${NETBIOSNSFILES}
	${TFTPFILES}
	${MQTTFILES}
	${MBEDTLS_FILES}
)

include_directories(${LWIPDIR}/include)

set(lwip_core_static_target "lwip-core-static")
set(lwip_app_static_target "lwip-app-static")
set(lwip_core_object_target "lwip-core-object")
set(lwip_app_object_target "lwip-app-object")

if(USE_STATIC_LWIP_LIBRARY)
    add_library(${lwip_core_static_target} STATIC ${LWIPNOAPPSFILES})
    set_target_properties(${lwip_core_static_target} PROPERTIES OUTPUT_NAME lwip-core-static)

    add_library(${lwip_app_static_target} STATIC ${LWIPAPPFILES})
    set_target_properties(${lwip_app_static_target} PROPERTIES OUTPUT_NAME lwip-app-static)
endif(USE_STATIC_LWIP_LIBRARY)

if(USE_OBJECT_LWIP_LIBRARY)
    add_library(${lwip_core_object_target} OBJECT ${LWIPNOAPPSFILES})
    set_target_properties(${lwip_core_object_target} PROPERTIES OUTPUT_NAME lwip-core-object)

    add_library(${lwip_app_object_target} OBJECT ${LWIPAPPFILES})
    set_target_properties(${lwip_app_object_target} PROPERTIES OUTPUT_NAME lwip-app-object)
endif(USE_OBJECT_LWIP_LIBRARY)

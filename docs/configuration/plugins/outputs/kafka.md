---
title: Kafka
weight: 200
generated_file: true
---

# Kafka output plugin for Fluentd
## Overview
  More info at https://github.com/fluent/fluent-plugin-kafka
>Example Deployment: [Transport Nginx Access Logs into Kafka with Logging Operator](../../../../quickstarts/kafka-nginx/)

 #### Example output configurations
 ```
 spec:
   kafka:
     brokers: kafka-headless.kafka.svc.cluster.local:29092
     default_topic: topic
     sasl_over_ssl: false
     format:
       type: json
     buffer:
       tags: topic
       timekey: 1m
       timekey_wait: 30s
       timekey_use_utc: true
 ```

## Configuration
### Kafka
#### Send your logs to Kafka

| Variable Name | Type | Required | Default | Description |
|---|---|---|---|---|
| brokers | string | Yes | - | The list of all seed brokers, with their host and port information.<br> |
| topic_key | string | No |  "topic" | Topic Key <br> |
| partition_key | string | No |  "partition" | Partition <br> |
| partition_key_key | string | No |  "partition_key" | Partition Key <br> |
| message_key_key | string | No |  "message_key" | Message Key <br> |
| client_id | string | No |  "kafka" | Client ID <br> |
| default_topic | string | No |  nil | The name of default topic .<br> |
| default_partition_key | string | No |  nil | The name of default partition key .<br> |
| default_message_key | string | No |  nil | The name of default message key .<br> |
| exclude_topic_key | bool | No |  false | Exclude Topic key <br> |
| exclude_partion_key | bool | No |  false | Exclude Partition key <br> |
| get_kafka_client_log | bool | No |  false | Get Kafka Client log <br> |
| headers | map[string]string | No |  {} | Headers <br> |
| headers_from_record | map[string]string | No |  {} | Headers from Record <br> |
| use_default_for_unknown_topic | bool | No |  false | Use default for unknown topics <br> |
| idempotent | bool | No |  false | Idempotent <br> |
| sasl_over_ssl | bool | Yes |  true | SASL over SSL <br> |
| username | *secret.Secret | No | - | Username when using PLAIN/SCRAM SASL authentication<br> |
| password | *secret.Secret | No | - | Password when using PLAIN/SCRAM SASL authentication<br> |
| scram_mechanism | string | No | - | If set, use SCRAM authentication with specified mechanism. When unset, default to PLAIN authentication<br> |
| max_send_retries | int | No |  1 | Number of times to retry sending of messages to a leader <br> |
| required_acks | int | No |  -1 | The number of acks required per request .<br> |
| ack_timeout | int | No |  nil => Uses default of ruby-kafka library | How long the producer waits for acks. The unit is seconds <br> |
| compression_codec | string | No |  nil | The codec the producer uses to compress messages . The available options are gzip and snappy.<br> |
| kafka_agg_max_bytes | int | No |  4096 | Maximum value of total message size to be included in one batch transmission. .<br> |
| kafka_agg_max_messages | string | No |  nil | Maximum number of messages to include in one batch transmission. .<br> |
| discard_kafka_delivery_failed | bool | No |  false | Discard the record where Kafka DeliveryFailed occurred <br> |
| ssl_ca_certs_from_system | *bool | No |  false | System's CA cert store <br> |
| ssl_ca_cert | *secret.Secret | No | - | CA certificate<br> |
| ssl_client_cert | *secret.Secret | No | - | Client certificate<br> |
| ssl_client_cert_chain | *secret.Secret | No | - | Client certificate chain<br> |
| ssl_client_cert_key | *secret.Secret | No | - | Client certificate key<br> |
| ssl_verify_hostname | *bool | No | - | Verify certificate hostname<br> |
| format | *Format | Yes | - | [Format](../format/)<br> |
| buffer | *Buffer | No | - | [Buffer](../buffer/)<br> |

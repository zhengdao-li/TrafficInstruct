# TrafficInstruct

**A Multi-Task Network Traffic Dataset and Benchmark for Instruction Tuning**

TrafficInstruct supports supervised fine-tuning and evaluation of large language models for network traffic analysis. It contains **55,000 structured SFT records across ten tasks**, together with the corresponding raw packet captures (PCAP files). The tasks cover threat detection and attribution, encrypted traffic analysis, website fingerprinting, and application classification under a controlled concept-drift setting.

This repository provides the dataset overview, access instructions, and citation information. **Dataset files are hosted on cloud storage and are available by email application. Download links and access codes are not published in this repository.**

## Dataset overview

- **Ten tasks:** a common instruction-based interface with task-specific traffic observations and structured prediction targets.
- **Raw PCAP and SFT data:** packet captures for traffic analysis and structured records for instruction tuning.
- **55,000 SFT records:** the Web attack task includes 5,000 plaintext and 5,000 encrypted observations; the two views belong to the same task.
- **Multiple label granularities:** coarse classification and fine-grained attribution where applicable.
- **Fixed evaluation partitions:** training, validation, and test partitions for benchmark comparison.

Traffic is collected from controlled software executions, attack experiments, and application activities. Labels are supported by collection records and task-specific evidence. Observations use task-appropriate units, including connections, flows, flow statistics, flow windows, and website-visit traces.

## Tasks

| Task | Abbreviation | Classification targets |
| --- | --- | --- |
| Malware Traffic Detection | MTD | Benign/malicious detection; benign and malware-family classification (11 fine classes) |
| Botnet Detection | BND | Normal/Botnet detection; Normal and five Botnet families (6 fine classes) |
| Malicious DNS-over-HTTPS Detection | MDD | Non-DoH/benign/malicious detection; 14-class category prediction |
| Web Attack Detection | WAD | Benign/attack detection; 9-class category prediction, with plaintext and encrypted views |
| APT Attack Detection | AAD | Benign/malicious flow classification |
| Encrypted VPN Detection | EVD | Normal/VPN detection; 18-class activity prediction |
| Tor Behavior Detection | TBD | Normal/Tor detection; 12-class activity prediction |
| Encrypted Application/Service Classification | EAC | Application/service identification (27 classes) |
| Website Fingerprinting | WF | Monitored/unknown detection; 50 monitored sites and an unknown class (51 fine classes) |
| Application Classification under Concept Drift | CD | Android application identification (12 classes), with P0–P4 for training/validation and P5 for testing |

The CD task evaluates application classification under a controlled behavior schedule. Its prediction target is application identity. TrafficInstruct's controlled collection settings do not cover the full diversity of operational networks.

## Data formats

The dataset includes:

1. **Raw packet captures:** PCAP files containing the captured network traffic.
2. **Supervised fine-tuning data:** structured records containing `instruction`, `input`, and `output` fields. Input representations and output schemas depend on the task.

The benchmark evaluates majority-class and random-forest baselines, ET-BERT, an unadapted 27B language model, and task-specific LoRA adapters on a shared frozen base. The plaintext and encrypted Web views use separately trained adapters. Please refer to the paper for task definitions, input preparation, evaluation rules, and experimental results.

## Request access

To apply for access to TrafficInstruct, email **[zhengdaoli@mail.ustc.edu.cn](mailto:zhengdaoli@mail.ustc.edu.cn)** with the subject:

```text
TrafficInstruct Dataset Access Request
```

Please include your name, affiliation, intended use of the dataset, and confirmation that you will cite the TrafficInstruct paper in publications using the dataset.

You may use the following email template:

```text
Subject: TrafficInstruct Dataset Access Request

Dear TrafficInstruct authors,

I would like to request access to TrafficInstruct.

Name:
Affiliation:
Intended use:
Requested materials: Raw PCAP / SFT data / Both

I agree to cite the TrafficInstruct paper in publications that use this dataset.

Best regards,
[Your name]
```

After reviewing your request, we will reply by email with the cloud-storage download link and access code for approved applications. Please use the download information provided in our reply.

## Paper and citation

**TrafficInstruct: A Multi-Task Network Traffic Dataset and Benchmark for Instruction Tuning**

Zhengdao Li, Hui Wen, Zixuan Wan, Weifeng Zhang, Yan Wu, Nenghai Yu, Weiming Zhang, and Kejiang Chen.

**If you use TrafficInstruct in a publication, you are required to cite our paper.**

```bibtex
@misc{li2026trafficinstruct,
  title  = {TrafficInstruct: A Multi-Task Network Traffic Dataset and Benchmark for Instruction Tuning},
  author = {Li, Zhengdao and Wen, Hui and Wan, Zixuan and Zhang, Weifeng and Wu, Yan and Yu, Nenghai and Zhang, Weiming and Chen, Kejiang},
  year   = {2026}
}
```

## Contact

School of Cyberspace Security, University of Science and Technology of China, Hefei, China.

For dataset access and questions, contact **[zhengdaoli@mail.ustc.edu.cn](mailto:zhengdaoli@mail.ustc.edu.cn)**.

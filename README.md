## Cloud Cost Optimization - AWS Cloud <br/>
About Cost Optimization techniques in AWS Cloud. Cloud Cost Optimization. <br/>

* [As per AWS Well-Architected frameworkCost Optimization pillar](https://wa.aws.amazon.com/wellarchitected/2020-07-02T19-33-23/wat.pillar.costOptimization.en.html) includes the ability to run systems to deliver business value at the lowest price point. <br/>
* Optimizing cloud costs isn't just about reducing costs; it's also about aligning costs with business goals. An increase in costs is not necessarily a problem if it's accompanied by an increase in revenue. One of the most important goals is to ensure that costs correlate with productive and profitable activities. <br/>
* There are three fundamental drivers of cost with AWS which should be kept in mind while architecting solutions  : compute, storage, and outbound data transfer. <br/>
* [Generic AWS Guidance on cost optimization](https://aws.amazon.com/aws-cost-management/aws-cost-optimization/)<br/>
* [AWS Cost Calculation example](https://docs.aws.amazon.com/whitepapers/latest/how-aws-pricing-works/cost-calculation-examples.html) are is a good place to start. It is essential to measure the benefit/efficiency of a workload by business to justify the costs associated with it. <br/>
* Upgrade instances to latest generation : They typically provide higher efficiency or better performance at a lower price. When AWS releases a new generation of instances, they tend to have improved performance and functionality compared to their predecessors. This means customers can either upgrade existing instances to the latest generation, or downsize existing instances with borderline utilization metrics in order to benefit from the same level of performance at lower cost.<br/>
* (Optimize storage) Delete unattached EBS volumes :a good practice is to check “delete on termination” box when an instance is launched. A simple AWS Lamda function can be writted to delete unused EBS volumes.<br/>
* (Optimize storage) Delete obsolete snapshots. <br/>
* Release unattached Elastic IP addresses : EIP's are free of change when attached to running service. Exceptions to the free of charge rule occur if customers remap an IP address more than 100 times a month, or if retain an unattached Elastic IP address after terminating the instances to which they were attached. AWS charges for such EIP's. <br/>
* (Optimize storage) Move infrequently-accessed data to lower cost tiers : Store production files in S3 and move them between storage tiers based on activity, or dynamically using S3 Smart Tiering. Archive infrequently used data in S3 Glacier and back up long-term archived data in Glacier Deep Archive. <br/>
* Schedule instances to ensure they run only during business hours or when needed. This is achieved automatically by using AWS Instance Scheduler or other tools. <br/>
* Terminate zombie assets : The term “zombie assets” is most often used to describe any unused asset contributing to the cost of operating in the AWS Cloud. Sometimes it may be diffcult to find all assets and 3rd party tools like VMWare CloudHealth can help. <br/>
* Tag AWS resources : Tagging helps to having a cost-conscious culture, establishing guardrails to meet financial targets, and gain greater business efficiencies. A good resource tagging policy can save costs. For example, resources with non-production tags can be de-provisioned or shut down in holidays or when not used. Tags helps to analyze and attribute expenditure. Tags makes it easier to accurately identify the usage and cost of systems, which then allows transparent attribution of IT costs to individual workload owners. This helps measure return on investment (ROI) and gives workload owners an opportunity to optimize their resources and reduce costs. Tagging resources increases the amount of data monitoring tools can obtain. <br/>
* Right size instances : The purpose of rightsizing is to match instance sizes to their workloads. This ensures substantial cost savings. <br/>
* Leverage the right pricing model : After selecting the correct size instance and creating elasticity through Auto Scaling or scheduling function, one can choose the correct pricing model. Reserved Instances are an excellent choice to save money and reduce the cost of the right workload. AWS provides Cost Explorer and Trusted Advisor to ensure that everyone can use the correct pricing model. AWS has [EC2 pricing models to choose](https://aws.amazon.com/ec2/pricing/) from on-demand instances, reserved instances, and spot instances.<br/>
* Increase elasticity : Cloud enables to optimize costs to meet dynamic needs, turning resources off when they are no longer needed.  This should be leveraged to the fullest. Customers can analyze EC2 instances with [AWS Compute Optimizer](https://aws.amazon.com/compute-optimizer/) and get data and receive reporting recommendations for right-sizing instances.<br/>
* Use the right volume type of Amazon EBS : where performance requirements are lower, using Amazon EBS Throughput Optimized HDD (st1) storage typically costs half as much as the default General Purpose SSD (gp2) storage option. [Details about every EBS volume type is available here.](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ebs-volume-types.html). <br/>
* Reduce data transfer costs : Data transfer from AWS resources creates significant expenditure. Consider using Amazon CloudFront CDN. Dynamic or static web content can usually be cached at Amazon CloudFront edge locations worldwide, and with this solution, customers can reduce the cost of data transfer out (DTO) to the public internet. Another good option is to reduce Public IP's in architecture. This is better for both cost and security perspective. <br/>
* Measure, monitor, and improve : As cloud environments are dynamic so measurements and monitoring for accurate visibility and continuous costs optimization is essential. One simple approach is defining and enforcing cost allocation tagging, define metrics and specific targets. <br/>
* Some native AWS Cost Optimization Tools and Services :
   * CloudWatch : One of the keys to reducing cloud bills is to have visibility into services. CloudWatch is a AWS tool for collecting and tracking metrics, monitoring log ﬁles, creation of resource alarms, and setting of an automatic reaction to changes in AWS resources. Metrics can be set up as and when required. <br/>
   * [AWS Cost Explorer](https://docs.aws.amazon.com/cost-management/latest/userguide/ce-what-is.html). <br/>
   * [AWS Trusted Advisor](https://aws.amazon.com/premiumsupport/technology/trusted-advisor/) :  Get real-time identiﬁcation of potential areas for optimization. One of the five areas checked by Trusted Advisor is cost optimization.It provides automated responses to - EC2 reserved instance optimization, Low utilization of EC2 instances, Idle elastic load balancers, Underutilized EBS volumes, Unassociated elastic IP addresses & Idle DB instances on Amazon RDS. <br/>
   * [AWS Budgets](https://aws.amazon.com/aws-cost-management/aws-budgets/) : Set custom budgets that trigger alerts when cost or usage exceed or are only forecasted to exceed a budgeted amount. Budgets can be set based on tags and accounts as well as resource types. <br/>
   * Amazon S3 analytics and Amazon S3 Storage Lens : Use [Amazon S3 analytics – Storage Class Analysis](https://docs.aws.amazon.com/AmazonS3/latest/userguide/analytics-storage-class.html) for automated analysis and visualization of Amazon S3 storage patterns to help  decide when to shift data to a different storage class. [Amazon S3 Storage Lens](https://aws.amazon.com/s3/storage-analytics-insights/) delivers organization visibility into object storage usage, activity trends, and makes recommendations to improve cost-efficiency and apply best practices. [This is the AWS video](https://www.youtube.com/watch?v=E2vy1yhJSHE)<br/>
   * Amazon S3 Intelligent-Tiering : Delivers automatic cost savings on S3 service by moving data between two access tiers: frequent access and infrequent access.<br/>
   * [AWS Auto Scaling](https://aws.amazon.com/autoscaling/) : Monitors applications and automatically adjusts resource capacity to maintain steady and predictable performance at the lowest possible cost. <br/>
   * [AWS Cost and Usage Report](https://docs.aws.amazon.com/cur/latest/userguide/what-is-cur.html) : After set-up, everyone can receive hourly, daily or monthly reports that break out of costs by product or resource and by tags that was defined . These report files are delivered to Amazon S3 bucket. <br/>
   * AWS Compute Optimizer : Recommends optimal AWS resources for your workloads to reduce costs and improve performance by using machine learning. AWS Compute Optimizer analyzes resource utilization to identify AWS resources, such as Amazon EC2 instances, Amazon EBS volumes, and AWS Lambda functions, that might be under-provisioned or over-provisioned.<br/>
   * AWS Instance Scheduler : This is a simple service that enables customers to easily configure custom start and stop schedules for their Amazon EC2 and Amazon RDS instances. <br/>


## Further References <br/>
* [How do I estimate the cost of my planned AWS resource configurations?](https://aws.amazon.com/premiumsupport/knowledge-center/estimating-aws-resource-costs/)<br/>
* [Key Principles : Fundamentals of AWS Pricing](https://docs.aws.amazon.com/whitepapers/latest/how-aws-pricing-works/key-principles.html)<br/>
* [AWS Cost Optimization - AWS Well-architected framework](https://wa.aws.amazon.com/wellarchitected/2020-07-02T19-33-23/wat.pillar.costOptimization.en.html)<br/>

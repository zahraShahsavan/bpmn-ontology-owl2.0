# Business Process Model and Notation Ontology

## 1. Overview
This ontology models core elements of a Business Process Model and Notation (BPMN) diagram in OWL 2. It defines classes for process‐related concepts (e.g., Activities, Events, Gateways), provides object properties to link these concepts (e.g., hasEvent, isPerformedBy), and uses data properties (like processName) to store simple string values. Additionally, it includes individuals (instances) that exemplify how real‐world BPMN nodes might be represented (e.g., a process called OrderApprovalProcess).

---

## 2. Classes (Domain Concepts)
Below is an explanation of every declared class and its intended meaning within a BPMN‐inspired model:

1. **Activities**  
   - Represents the notion of BPMN activities, such as tasks or sub‐processes.

2. **Agent**  
   - A superclass for any entity capable of performing an activity (e.g., Human, Software).

3. **Annotation**  
   - Corresponds to BPMN “annotations” or textual notes attached to the diagram.

4. **AssociationFlow**  
   - A specialized connecting element used for associating artifacts, e.g., linking an annotation to an activity.

5. **ConnectingElements**  
   - A general class for flow constructs such as association flows, sequence flows, etc.

6. **Data**  
   - A broad class covering any BPMN data constructs (DataObject, DataInput, DataStore, etc.).

7. **DataAssociation**  
   - Another connecting element that associates a piece of data to an activity or event.

8. **DataInput**  
   - A special data artifact representing input required for an activity.

9. **DataObject**  
   - A BPMN data object, often signifying a document or piece of info needed by the process.

10. **DataOutput**  
    - A data artifact representing output produced by an activity.

11. **DataStore**  
    - A persistent data element, e.g., a database or system of record.

12. **EndEvent**  
    - A type of BPMN event marking the end of a process flow.

13. **EventBasedGateway**  
    - A BPMN gateway that routes based on events.

14. **Events**  
    - A generic class for BPMN events (Start, Intermediate, End).

15. **Flow**  
    - The general concept of a flow element in BPMN.

16. **Gateway**  
    - A BPMN gateway controlling divergence or convergence of the sequence flow.

17. **Group**  
    - A grouping artifact to visually group diagram elements.

18. **Human**  
    - Subclass of Agent denoting that an activity is performed by a person.

19. **IntermediateEvent**  
    - An event occurring between start and end of the process flow.

20. **MessageFlow**  
    - A flow of messages between pools or processes.

21. **Node**  
    - A generic node in the BPMN graph, extended by Activities, Events, etc.

22. **ParallelGateway**  
    - A gateway that executes paths in parallel.

23. **Pools**  
    - Represent BPMN pools (swimlanes at a higher level).

24. **ReceiveTask**  
    - A specialized BPMN task that waits for a message.

25. **SendTask**  
    - A specialized BPMN task that sends a message.

26. **SequenceFlow**  
    - A flow that connects BPMN elements in sequence.

27. **ServiceTask**  
    - A specialized BPMN task performed by a service (software or machine).

28. **Software**  
    - Subclass of Agent, representing an automated performer.

29. **StartEvents**  
    - A specialized event marking the start of a process.

30. **SubProcess**  
    - An activity that itself contains a lower‐level process flow.

31. **Task**  
    - A generic BPMN task (atomic activity).

32. **UserTask**  
    - A BPMN task performed by a human user (as opposed to a system).

33. **lanes**  
    - Typically representing BPMN swimlanes inside a pool.

---

## 3. Object Properties
Each object property connects two individuals:

1. **hasDataObject**  
   - **Domain**: Activities  
   - **Range**: Data  
   - Means “this activity uses or is associated with that data object.”

2. **hasEvent**  
   - **Domain**: Activities  
   - **Range**: Events  
   - Means “this activity has (or is linked to) a BPMN event” (e.g., an end event).

3. **hasStartEvent**  
   - Declared a sub‐property of **hasEvent**.  
   - **Domain**: Activities  
   - **Range**: Events  
   - Specifically indicates “this activity has a start event.”

4. **hasEndEvent**  
   - New property, also declared as a sub‐property of **hasEvent**.  
   - **Domain**: Activities  
   - **Range**: Events  
   - Specifically indicates “this activity has an end event.”

5. **isPerformedBy**  
   - **Domain**: Activities  
   - **Range**: Agent  
   - Denotes who or what performs the activity (e.g., a human or software).

---

## 4. Data Property

1. **processName**  
   - **Domain**: Activities  
   - **Range**: xsd:string  
   - A simple data property that stores the textual name of the activity or process (e.g., “Order Approval Workflow”).

---

## 5. Individuals (Instances)
Below are the named individuals that exemplify usage of the classes and properties:

1. **Alice**  
   - Declared a member of **Human**, meaning Alice is a person (an Agent).

2. **ApprovalEndEvent**  
   - Declared a member of **EndEvent**, signifying a BPMN End Event named “ApprovalEndEvent.”

3. **ApprovalForm**  
   - Declared a member of **DataObject**, representing some form or document used in the process.

4. **CheckDocumentsTask**  
   - Declared a member of **UserTask**, indicating a user (human) is meant to check documents.  
   - Related to Alice via **isPerformedBy(CheckDocumentsTask, Alice)**.

5. **OrderApprovalProcess**  
   - Declared a member of **Activities**.  
   - Has a data property **processName("Order Approval Workflow")**.  
   - Linked to **ApprovalEndEvent** by **hasEvent(OrderApprovalProcess, ApprovalEndEvent)**.  
   - Linked to **StartEvent_1** by **hasStartEvent(OrderApprovalProcess, StartEvent_1)**.  
   - Linked to **ApprovalEndEvent** by **hasEndEvent(OrderApprovalProcess, ApprovalEndEvent)** (the new property).

6. **StartEvent_1**  
   - Declared a member of **StartEvents**, representing a BPMN start event.

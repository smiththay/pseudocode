# PseudoCode:Elevator

## OBJECTIVE
As an individual you want to go from your current floor to a desired floor.

## Elevator Parts

![parts](https://github.com/smiththay/pseudocode/blob/dev/img/elevatorparts.jpg)


## BASIC STEPS
- Individual can step in and out of the elevator
- Individual can input direction, desired floor number, whether to open and close elevator doors, or if there is an emergency
- The elevator can go up and go down
- The elevator can open and close its doors
- The current floor has a floor panel to tell the elevator controller the desired direction of travel
- The car panel will tell the elevator controller which floor is desired, whether or not the doors can open or close, or if there is an emergency
- The elevator display will show the direction of travel and the current floor the elevator is on

## START

**PROGRAM** Elevator 

**INIT**
- Individual
- ElevatorCar
- ElevatorController
- ElevatorDoor
- ElevatorDisplay
- FloorPanel
- CarPanel 

**Elevator Controller**
	
    COMPUTE
		Elevator Functions 
	
    DETERMINE
		Current Floor of ElevatorCar
		Which floor to travel to if FloorPanel value is selected
		When to stop at selected FloorNumber

**FloorPanel**
	
    SET
		UpArrow Button//Destination is above current floor
		DownArrow Button//Destination is below current floor

**CarPanel**
	
    SET
		FloorNumber Buttons// Individual chooses from array to tell controller selected floor
		OpenDoor Button
		CloseDoor Button
		EmergencyAlarm Button

**ElevatorDisplay**
	
    FOR  
		Every floor ElevatorCar is on DISPLAY  current floor                               
 	
	WHILE
		ElevatorCar travels up DISPLAY arrow pointing up
		ElevatorCar travels down DISPLAY arrow pointing down

**Individual**
	
    INPUT
		Value on FloorPanel
		Value on CarPanel

	FUNC StepIN
	
    	IF
			 ElevatorDoor is open && Individual has not reached desired floor then step in
		ELSE
			don’t move

	FUNC StepOut
	
    	IF
			ElevatorDoor is open && Individual has reached desired floor then step out
		ELSE 
			don’t move

**ElevatorCar**
	
	Function TravelUp
	
    	INPUT
			UpArrow on FloorPanel 
			FloorNumber from FloorArray on CarPanel
		IF
			ElevatorCar is on floor below selected FloorPanel &&
			ElevatorDoors are closed
		ELSE IF
			FloorNumber selected is above CurrentFloor && ElevatorDoors are closed
		THEN 
			ElevatorCar travels up
		ELSE
			Stay on CurrentFloor
		WHILE
			ElevatorCar is traveling down
			TravelDown Function is completed		

	Function TravelDown
	
    	INPUT	
			DownArrow on FloorPanel
			FloorNumber from FloorArray on CarPanel
		IF
			ElevatorCar is on a floor above selected FloorPanel && 	ElevatorDoors are closed
		ELSE IF
			FloorNumber selected is below CurrentFloor && ElevatorDoors are closed
		THEN 
			ElevatorCar travels down
		ELSE 
			Stay on CurrentFloor
		WHILE
			ElevatorCar is traveling up 
			TravelUp Function is completed

**Elevator Doors**

	Function DoorOpen
	
    	IF
			ElevatorCar has reached SelectedFloor 
		ELSE IF 
			OpenDoor button is pushed && is at SelectedFloor 
		ELSE IF
			 Individual is in doorway
		THEN 
			Door Opens
		ELSE
			 remains closed
		WHILE
			ElevatorCar is traveling ElevatorDoor remains closed

	Function DoorClose
	
    	IF
			ElevatorCar has reached SelectedFloor && doors have been opened for (x) amount of time 
		ELSE IF
			CloseDoor button is pushed && doors have been opened for (x) amount of time
		ELSE
			remains open
		THEN
			Door Closes
		WHILE 
			ElevatorCar is traveling ElevatorDoors remains closed

**EXCEPTION**
	
    WHEN
		ElevatorCar stops in-between floors || ElevatorDoors won’t open	at a floor
			INPUT
				EmergencyAlarmButton

## END
